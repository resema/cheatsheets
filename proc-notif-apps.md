# Outtake of some DSCore Concepts <!-- omit in toc -->
### Table of Content <!-- omit in toc -->

- [1. Introduction](#1-introduction)
  - [1.1. Team lead](#11-team-lead)
  - [1.2. General Links](#12-general-links)
- [2. Procedure & Step Services](#2-procedure--step-services)
  - [2.1. General](#21-general)
  - [2.2. Usage](#22-usage)
    - [2.2.1. Pseudo code](#221-pseudo-code)
  - [2.3. Additional Links](#23-additional-links)
- [3. Notifications](#3-notifications)
  - [3.1. General](#31-general)
  - [3.2. Usage](#32-usage)
    - [3.2.1. `notification` Service](#321-notification-service)
      - [3.2.1.1. Pseudo Code](#3211-pseudo-code)
    - [3.2.2. `notification-storage` Service](#322-notification-storage-service)
      - [3.2.2.1. Pseudo Code](#3221-pseudo-code)
    - [3.2.3. Widget, Page or other part in Frontend](#323-widget-page-or-other-part-in-frontend)
      - [3.2.3.1. Pseudo Code](#3231-pseudo-code)
- [4. Integration into App](#4-integration-into-app)
  - [4.1. Existing Widgets](#41-existing-widgets)

---
---
# 1. Introduction
  
## 1.1. Team lead
- Procedure: alexander.treptow@freiheit.com
- Step: alexander.treptow@freiheit.com
- Notification: michael.grosshans@freiheit.com; alexander.treptow@freiheit.com
- Notification-Storage: alexander.treptow@freiheit.com
- Media Library: benedict.jost@freiheit.com
- Storage & Sync: benedict.jost@freiheit.com

## 1.2. General Links
- https://wiki.dentsplysirona.com/display/LIGAL/Lightning+Architecture+Diagram

- https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/doc
  
- https://wiki.dentsplysirona.com/display/LIGPEN/01.+Getting+Started
- https://wiki.dentsplysirona.com/display/LIGPEN/03.+Registered+Treatments+and+Procedures
- https://wiki.dentsplysirona.com/display/CW/Integrating+into+Lightning-Core+App


---
---
# 2. Procedure & Step Services
## 2.1. General
- offers the possibility for teams to create
  - threatments
  - procedures
  - steps
    - with customized input/output conditions
- separated into two services
  
## 2.2. Usage
- follow the example, f.ex. `dummy-extension` or `dummy-scan`
- implement the `cas-interface.proto`
  - https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/procedure/cas-interface.proto
    - `Start`
    - `GetSteps`
    - more
- use the `api.proto` from procedure and step service
  - https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/procedure/api.proto
    - `RegisterDefinition`
    - `UpdateProcedure`
    - `CreateProcedure`
  - https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/step/api.proto
    - `RegisterDefinition`
    - `UpdateStep`
    - more

### 2.2.1. Pseudo code
```cpp
#include <procedure>
#include <step>

main {
    // get clients
    procedureClient = procedure.NewClient()
    stepClient      = step.NewClient()

    // provide the cas service interface
    RegisterCASServiceServer(...)

    // define Procedure
    id = procedureClient.RegisterDefinition()

    // define steps
    steps = stepAPI.StepDefinition( step1, step2, step3 ) 
    stepClient.RegisterDefinition( steps )

    // creation
    procedureClient.CreateProcedure( id )

    // step-by-step
    stepClient.UpdateStep()

    // change procedure state, f.ex. finished
    procedureClient.UpdateProcedure( state )
}
```

## 2.3. Additional Links
- https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/doc/procedure_implementation.md
- https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/procedure/procedure-composition.md
- https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/procedure/recommended-procedures.md
- https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/procedure/register-procedure.md
- https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/procedure/start-procedure.md
- https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/procedure/update-procedure-state.md
- https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/procedure/steps.md

---
---
# 3. Notifications
## 3.1. General
- 2 possible services
  - `notification`
    - notifies FE
    - topics are defined in FE and BE
      - strings, must match
  - `notification-storage`
    - stores permanently notifications from other BE services
    - uses `notification` service
    - user must confirm the notifications
      - reloading of the page possible

## 3.2. Usage
### 3.2.1. `notification` Service
- examples are 
  - `order` service -> uses accountId as topic
  - `cerec_converter` service -> uses custom strings for topics (conversionStarted, conversionFinished, ...)
- use notification interface
  - https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/notification/api.proto
    - `PublishNotification`
    - `UnsafePublishNotification`
- define topic for publishing

#### 3.2.1.1. Pseudo Code
```cpp
#include <notification>

main {
    // define topic
   topics = "scan_started", "scan_success", "scan_failed"

    // get client
    notificationClient = notification.NewClient()

    // send notification
    notificationClient.PublishNotification( topic[1] )
}
```

### 3.2.2. `notification-storage` Service
- use notification-storage service interface
  - https://bitbucket.dentsplysirona.com/projects/LIG/repos/lightning-core/browse/services/notification-storage/api.proto
  - `CreateNotification`
- publishes currently to the topic `userName`

#### 3.2.2.1. Pseudo Code
```cpp
#include <notification-storage>

// notification-storage must know datatype to handle their storage in db
// -> extend API of notification-storage if new service wants to use it

main {
    // get client
    notificationStorageClient = notificationStorage.NewClient()

    // some content
    content = notificationStorageClient.NotificationBody({
        id, state
    })

    // send notification
    notificationStorageClient.CreateNotification( content )
}
```

### 3.2.3. Widget, Page or other part in Frontend
- use `public_package_notification.dart`
  - provides NotificationClient interface, `notification.dart`
    - `subscribe`
    - `unsubscribe`
    - and more
  - subscribe to same topic
- use `common/lib`
  - from folder `models`
    - `NotificationData` for creating a toast
  - from folder `interfaces`
    - `toaster`

#### 3.2.3.1. Pseudo Code
```cpp
import 'package:public_package_notification'

/// a class representing some state which triggers
/// a toast in case of receiving a notification
class MyMediaState {
    /// client
    NotificationClient notificationClient

    /// subscription
    void subscribeMyMediaNotification() {
        notificationClient.subscribe(
            topic,
            (message) => onMyMediaNotification( message )
        )
    }

    /// callback
    async onMyMediaNotification( message ) {
        newNotification = NotificationData.create( content )

        // show toaster
        toasterState.notifiy(newNotification)
    }
}
```

---
---
# 4. Integration into App
- decide if new page, new app, integration in existing code, others
- communicate through RESTApi with backend
- Add a Dependency to Your Procedure in `pubspec.yaml`
- Register your procedure in `build.yaml`
  - integration of localization, assets

## 4.1. Existing Widgets
- DSM provides a overview of existing widgets
  - Modal Dialog: https://dentsplysirona.invisionapp.com/dsm/dentsply-sirona/ds-core/nav/5fa7cb0a8c0120001835494d/asset/60818a50457d8c61fd2ff294/tab/design?mode=preview&version=6274b8d02eebc04b81304a5e
