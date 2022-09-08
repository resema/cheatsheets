# Localization <!-- omit in toc -->
- [1. Situation](#1-situation)
  - [1.1. Current Situation](#11-current-situation)
  - [1.2. Vision of Future](#12-vision-of-future)
- [2. Questions](#2-questions)
  - [Q1: How to align with domain's monorepo structure?](#q1-how-to-align-with-domains-monorepo-structure)
  - [Q2: How are multiple products from a single domain handled?](#q2-how-are-multiple-products-from-a-single-domain-handled)
  - [Q3: How to align with versioning schemes?](#q3-how-to-align-with-versioning-schemes)
  - [Q4: What's the migration overhead for existing products?](#q4-whats-the-migration-overhead-for-existing-products)
- [3. Answers](#3-answers)
    - [A1: Per product a dedicated Flutter app](#a1-per-product-a-dedicated-flutter-app)
    - [A2: Every product has dedicated localization folder and library](#a2-every-product-has-dedicated-localization-folder-and-library)
    - [A3: No special handling needed](#a3-no-special-handling-needed)
    - [A4: Splitting and renaming in some areas needed](#a4-splitting-and-renaming-in-some-areas-needed)
- [4. Conclusion](#4-conclusion)
- [5. Discussions](#5-discussions)
      - [5.0.0.1. Variante 1:](#5001-variante-1)
      - [5.0.0.2. Variante 2:](#5002-variante-2)
- [6. Folder structure](#6-folder-structure)
- [7. Example keys](#7-example-keys)

# 1. Situation

## 1.1. Current Situation
- Dev enters key and english text to the `app_de.arb`
- Trigger make target to build all necessary files
- Invite a translator to formulate other langugages
- Dev has to merge those changes to his branch
- Generator `DSAppLocalizations` uses per default 'en'

---

## 1.2. Vision of Future
- 1x Figma Project per product
- Dev/Figma enters key in Localize
- Lokalize generates `arb` and/or new entries in existing `arb` file
- Dev has to rebase with PR from Tool
- The workflow is defined here: [WI-Translation Mangement](https://wiki.dentsplysirona.com/display/DPSDPH/WI+-+Translation+Management)

---
---
# 2. Questions
## Q1: How to align with domain's monorepo structure?
## Q2: How are multiple products from a single domain handled?
## Q3: How to align with versioning schemes?
## Q4: What's the migration overhead for existing products?

---
---
# 3. Answers
### A1: Per product a dedicated Flutter app
1. Single domain flutter apps are developed within the monorepo of the respective domain
2. Flutter apps with contributions from multiple domains are developed within the repository of the domain which is responsible for the main part of the app. Packages for the app from other domains are developed in that same repo. (I.e. we are choosing the Single-app monorepo approach from above)
3. We will have repositories with shared libraries which are used by several separate flutter apps. A current example for this is the Core UI widget library. These libraries are each maintained in a separate repository.
4. Every product has a dedicated Flutter application with a dedicated folder of localization files and a referencing library to use in code.

### A2: Every product has dedicated localization folder and library 
There are two variants discussed:
1. having per monorepo one localization folder and library and tag the keys with a product prefix
2. Each product has a dedicated localization folder and library

#### Variante 1: <!-- omit in toc -->
![simplified graphic](/out/diags/l10n/simplification/simplification.svg) <!-- omit in toc -->
```sh
# Folder structure
apps
└───l10n
│   └───lib
│   │   │   l10n.dart
│   │   └───l10n
│   │   │   │   app_en.arb    
│   │   │   │   app_de.arb
│   │   │   │   app_es.arb
│   │   │   │   app_fr.arb
│   │   │   │   ...
│   │   │   └───generated
│   │   │   │   │   app_localization_en.dart
│   │   │   │   │   app_localization_de.dart
│   │   │   │   │   app_localization_es.dart
│   │   │   │   │   app_localization_fr.dart
│   │   │   │   │   ...


# Example keys with prefixing
app_en.dart
{
  "DSCoreDealerGetPopulatedDemoAccountHint": "Name for demo user account",
  # ...

  "BackofficeDashboardPageSharesPlaceholderTitle": "Share media with others",
  # ...
}
```

#### Variante 2: <!-- omit in toc -->
![simplified graphic alternative](/out/diags/l10n/simplification-alt/simplification-alt.svg) <!-- omit in toc -->
```sh
# Folder structure for localization files and libraries
apps
└───l10n-dscore
│   └───lib
│   │   │   l10n.dart
│   │   └───l10n
│   │   │   │   app_en.arb    
│   │   │   │   app_de.arb
│   │   │   │   app_es.arb
│   │   │   │   app_fr.arb
│   │   │   │   ...
│   │   │   └───generated
│   │   │   │   │   app_localization_en.dart
│   │   │   │   │   app_localization_de.dart
│   │   │   │   │   app_localization_es.dart
│   │   │   │   │   app_localization_fr.dart
│   │   │   │   │   ...
└───l10n-outsim
│   └───lib
│   │   │   l10n.dart
│   │   └───l10n
│   │   │   │   app_en.arb    
│   │   │   │   app_de.arb
│   │   │   │   app_es.arb
│   │   │   │   app_fr.arb
│   │   │   │   ...
│   │   │   └───generated
│   │   │   │   │   app_localization_en.dart
│   │   │   │   │   app_localization_de.dart
│   │   │   │   │   app_localization_es.dart
│   │   │   │   │   app_localization_fr.dart
│   │   │   │   │   ...

# Example keys
dscore_en.dart
{
  "backofficeDealerGetPopulatedDemoAccountHint": "Name for demo user account",
  "dashboardPageSharesPlaceholderTitle": "Share media with others",
}
```

### A3: No special handling needed
Our versioning approach differentiates between three schemes for versioning:
- Build artifact versioning, including
  - Microservices
  - Frontends
  - Shared libraries and other distribution packages
- Microservice API versioning
- Software product versioning
- Any build artifact is versioned using a `MAJOR.MINOR.PATCH` semantic scheme.

There is no special handling needed for the localization files in regards of versioning.


### A4: Splitting and renaming in some areas needed
1. The monorepo of transaction platform contains 3 flutter applications (dscore, sidexis and backoffice) which have all the same l10n folder and library
   1. Split into three l10n's
   2. current `DSAppLocalizations` class has to be split and renamed to the dedicated localization files and libraries, such as:
      - `DSCoreLocalizations`
      - `BackofficeLocalizations`
      - and more
2. Other products have already a single flutter application.

---
---
# 4. Conclusion
To facilitate the workflow from "UX &rarr; Translation &rarr; Development &rarr; Product" the approach that for every product a dedicated flutter app and a dedicated localization folder and library is to be used.

Domains which develop multiple Flutter application (each for a dedicated product) should have different localization folders and library for each product/Flutter app.

#### Example: <!-- omit in toc -->
![simplified graphic alternative](/out/diags/l10n/simplification-alt/simplification-alt.svg)
```sh
# Folder structure for localization files and libraries
apps
└───l10n-dscore
│   └───lib
│   │   │   l10n.dart
│   │   └───l10n
│   │   │   │   app_en.arb    
│   │   │   │   app_de.arb
│   │   │   │   app_es.arb
│   │   │   │   app_fr.arb
│   │   │   │   ...
│   │   │   └───generated
│   │   │   │   │   app_localization_en.dart
│   │   │   │   │   app_localization_de.dart
│   │   │   │   │   app_localization_es.dart
│   │   │   │   │   app_localization_fr.dart
│   │   │   │   │   ...
└───l10n-backoffice
│   └───lib
│   │   │   l10n.dart
│   │   └───l10n
│   │   │   │   app_en.arb    
│   │   │   │   app_de.arb
│   │   │   │   app_es.arb
│   │   │   │   app_fr.arb
│   │   │   │   ...
│   │   │   └───generated
│   │   │   │   │   app_localization_en.dart
│   │   │   │   │   app_localization_de.dart
│   │   │   │   │   app_localization_es.dart
│   │   │   │   │   app_localization_fr.dart
│   │   │   │   │   ...
```
```dart
/// Localizations for the DSCore app
class DSCoreLocalizations {
  /// ...
}

/// Localizations for the Backoffice app
class BackofficeLocalizations {
  /// ...
}
```

---
---
# 5. Discussions
### Florian Sobirey, Sept. 05 <!-- omit in toc -->
- pro product -> 1x Figma/Localize project
  - f.ex. UI for assistents and UI for service technician
- Redesign could lead to reuse of existing keys
- Version push to Bitbucket
  - [ ] keep same version possible with figma, localize and bitbucket?
- [ ] Naming convention for keys
  - [ ] prod_topic_frame_key

### Simon Egg, Sept. 05 <!-- omit in toc -->
#### Variante 1: Only One Localization File pro Language <!-- omit in toc -->
![simplified graphic](/out/diags/l10n/simplification/simplification.svg) <!-- omit in toc -->
- **not usable for &rarr; every app == product**

#### Variante 2: Multiple Localization File pro Language <!-- omit in toc -->
![simplified graphic alternative](/out/diags/l10n/simplification-alt/simplification-alt.svg) <!-- omit in toc -->
=======

### Analysis Alexander Treptow, Sept. 07 <!-- omit in toc -->
- configuration supports only, that every language is only one time available
- possible to use multiple packages
  - overhead for BuildContext
    - multiple sources needs a mechanism
- [] lightning repo contains currently 3 flutter aps
  - dscore, backoffice and sidexis
    - [ ] currently only one `l10n` folder
    - [ ] must be splitted in that case

### Ruwen Schnabel, Sept. 07 <!-- omit in toc -->
- [ ] 1x l10n folder per app
- [x] every app in one single product
- [ ] structuring
  - [ ] split arb files in folder into specific domains *or*
  - [ ] add prefixes to keys
- [x] Branching not wanted so far 

#### 5.0.0.1. Variante 1:
- having 1x `l10n` folder per app and therefor per product
- having 1x `arb` file per language
- prefixing `keys` with domain, product or likewise
  
```sh
# Folder structure
apps
└───l10n
│   └───lib
│   │   │   l10n.dart
│   │   └───l10n
│   │   │   │   app_en.arb    
│   │   │   │   app_de.arb
│   │   │   │   app_es.arb
│   │   │   │   app_fr.arb
│   │   │   │   ...
│   │   │   └───generated
│   │   │   │   │   app_localization_en.dart
│   │   │   │   │   app_localization_de.dart
│   │   │   │   │   app_localization_es.dart
│   │   │   │   │   app_localization_fr.dart
│   │   │   │   │   ...

# Example keys without prefixing
app_en.dart
{
  "backofficeDealerGetPopulatedDemoAccountHint": "Name for demo user account",
  "dashboardPageSharesPlaceholderTitle": "Share media with others",
}

# Example keys with prefixing
app_en.dart
{
  "DSCoreBackofficeDealerGetPopulatedDemoAccountHint": "Name for demo user account",
  "OutsimDashboardPageSharesPlaceholderTitle": "Share media with others",
}
```

#### 5.0.0.2. Variante 2:
- having 1x `l10n` folder per app and therefore per product
- having nx `lib` per domain, product or likewise
  
```sh
# 6. Folder structure
apps
└───l10n-dscore
│   └───lib
│   │   │   l10n.dart
│   │   └───l10n
│   │   │   │   app_en.arb    
│   │   │   │   app_de.arb
│   │   │   │   app_es.arb
│   │   │   │   app_fr.arb
│   │   │   │   ...
│   │   │   └───generated
│   │   │   │   │   app_localization_en.dart
│   │   │   │   │   app_localization_de.dart
│   │   │   │   │   app_localization_es.dart
│   │   │   │   │   app_localization_fr.dart
│   │   │   │   │   ...
└───l10n-outsim
│   └───lib
│   │   │   l10n.dart
│   │   └───l10n
│   │   │   │   app_en.arb    
│   │   │   │   app_de.arb
│   │   │   │   app_es.arb
│   │   │   │   app_fr.arb
│   │   │   │   ...
│   │   │   └───generated
│   │   │   │   │   app_localization_en.dart
│   │   │   │   │   app_localization_de.dart
│   │   │   │   │   app_localization_es.dart
│   │   │   │   │   app_localization_fr.dart
│   │   │   │   │   ...

# 7. Example keys
dscore_en.dart
{
  "backofficeDealerGetPopulatedDemoAccountHint": "Name for demo user account",
  "dashboardPageSharesPlaceholderTitle": "Share media with others",
}
``` -->
