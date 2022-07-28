# Glossary <!-- omit in toc -->
### Table of Content <!-- omit in toc -->

- [1. Procedure Service](#1-procedure-service)
  - [1.1. General](#11-general)
    - [1.1.1. Examples](#111-examples)
  - [1.2. APIs](#12-apis)
    - [1.2.1. Public API](#121-public-api)
  - [1.3. Dev Hints](#13-dev-hints)
  - [1.4. Extensions](#14-extensions)
    - [1.4.1. OnPremise CAM Mapping](#141-onpremise-cam-mapping)
  - [1.5. TODOs](#15-todos)
  
---
---
# 1. Procedure Service
## 1.1. General

Every CAS procedure service must:
- register a definition in this service, using the "RegisterDefinition" endpoint.
- implement the CAS-interface API.
- add information about the procedure definitions in the wiki page.
  see: https://wiki.dentsplysirona.com/display/LIGPEN/03.+Registered+Treatments+and+Procedures.

### 1.1.1. Examples

There are 3 examples on how to create a CAS procedure service, see: `services/dummy-aligner`, `services/dummy-cam` and `services/dummy-scan`.

---
## 1.2. APIs
### 1.2.1. Public API

``` protobuf
rpc RegisterDefinition (RegisterDefinitionReq) returns (RegisterDefinitionResp) {}

rpc UpdateProcedure (UpdateProcedureReq) returns (UpdateProcedureResp) {}

rpc CreateProcedure (CreateProcedureReq) returns (CreateProcedureResp) {}

// Output only. An instance of a procedure, being performed for a specific patient in a
// specific clinic. This does not include procedure-specific state, which will
// be kept by the CAS service.
message Procedure {
  // The ID of the procedure.
  string id = 1;
  // The ID of the procedure definition.
  string definition_id = 2;
  // The ID of the patient.
  string patient_id = 3;
  // The timestamp of the last time the procedure was updated.
  google.protobuf.Timestamp updated_at = 4;
  // The current state of the procedure (started, finished etc.).
  ProcedureState state = 5;
  // The text that should be shown as the "procedure" in the app.
  string active_procedure = 6;
  // The text that should be shown as the "procedure step" in the app.
  string active_step = 7;
  // The ID of this procedure's parent procedure, if it exists.
  string parent_id = 8;
  // The ID of the currently active descendant procedure of this procedure.
  string active_procedure_id = 9;
  // The ID of the user currently assigned to this procedure.
  string assignee_id = 10;

  // TODO add current and next step information
}
```

---
## 1.3. Dev Hints

- Registers a procedure definition. Re-registering a procedure with the same ID overwrites it.

- A procedure will be created with the 'Pending' state. In order to be considered an active procedure (eg. Started), the state must be updated by the CAS service. Creating a procedure will automatically initialize the first step of a procedure.

- `api.go` implements protos from `api.proto`, `internal.proto`

---
## 1.4. Extensions
### 1.4.1. OnPremise CAM Mapping

- The procedures of type ‘On Premise Production’ are not created for a specific user, but for the whole account. I am not sure how this shall end up in the list of tasks.
  
  ***starts needs the initial user. handover possible...***

  ***Dummy-account???***

  ***separate UI?***
  Separate list possible through list registered procedures

- Each procedures is assigned to exactly one DS Core patient. This causes the following issues:
  - There is a ‘patient field’ for an on premise production restoration. How can we match it to a DS Core patient?
  
    ***Should be discussed with S&S, because they handle patient data from PMS***
  
  - There may be more than one restorations from different patients in one production process. However, we’d like to map one production process to a procedure. What to do? One procedure for each patient? Then, how to eliminate duplicates in the task list? Is NOT providing a patient ID in case of ambiguities a simple yet working solution?
    
    ***Procedure has always only one patient. Procedure contains multiple procedures?***
    other patients for child procedures
    parent procedure w/o patientID (threatment)
    - [ ] anpassungen nötig

    account vs user -> account with corresponding user
    - [ ] Fallback to owner

    Possible to show all tasks -> yes

    - [ ] additional list for null patient

---
## 1.5. TODOs

- [ ] `CreateProcedure` returns _NOT_ nothing in case of success. Correct comment.
- [ ] Implication of patient zero
