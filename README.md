# Open UI Initiative - Framework Repo

NASWA, in partnership with the U.S. Department of Labor, is collaborating with state workforce agencies and other groups to strengthen the unemployment insurance (UI) system with a focus on how modern technology and digital practices can make state systems more accessible, resilient and secure.

The Open UI Initiative will change how we create and purchase technology. It involves forming new collaborations and partnerships to make a wider range of open and modular solutions available.

The purpose of this repository is to host the Open UI Framework, define the modules within it, and how a standardized data schema supports those modules. We will evolve the Framework over time with community support whether that is changing module boundaries, adapting interactions between modules, or optimizing a module’s outputs for new standards and technologies. Please review our [Code of Conduct](https://github.com/NASWA-OpenUI/Open-UI-Framework/blob/578fe338c2d225291c0f16338d57cec465c7a7f1/Contribution%20Guidelines/CODE_OF_CONDUCT.md).

To find [top-level information on Open UI](https://github.com/NASWA-OpenUI/Overview/blob/main/About%20the%20Initiative.md) and answers to [frequently asked questions](https://github.com/NASWA-OpenUI/Overview/blob/main/FAQs.md) please visit our [Overview Repository](https://github.com/NASWA-OpenUI/Overview).

Find more information and updates on Open UI at our [website](https://www.naswa.org/open-ui-initiative) or email us at [openui@naswa.org](mailto:openui@naswa.org).

<br>

## Table of Contents

1. [What is the Open UI Framework?](#what-is-the-open-ui-framework)
2. [How to contribute to or support the Open UI Initiative](#how-to-contribute-to-or-support-the-open-ui-initiative)

<br>

## What is the Open UI Framework?

### Introduction 

One of the objectives of the Open Unemployment Insurance (UI) Initiative is to define and evolve a standardized modular UI technology framework. We anticipate the Open UI Framework will become the standard topography of UI systems throughout the field. To learn more about the initiative, please see our About the Initiative page. 

The Open UI Framework defines key groups of functionalities or system boundaries as “modules.” The complete [Open UI Module Set](https://github.com/NASWA-OpenUI/Open-UI-Framework/blob/57f6916334e1470ff98275a043ea4591006db56e/Open%20UI%20Initiative%20Module%20Set.md) is the minimum set of modules needed to fully support the administration of UI. For each of these modules, it specifies data and interface standards for interacting with the rest of a UI system. 

This document discusses the Open UI Framework, how modules are defined within it, and how a standardized data schema supports those modules. With input from the Open UI Community, we will evolve the Open UI Framework over time, whether that is changing module boundaries, adapting interactions between modules, or optimizing a module’s outputs for new standards and technologies.   

### Description 

The Open UI Framework breaks down into three main bodies of work: 
* The [**Open UI Module Set**](https://github.com/NASWA-OpenUI/Open-UI-Framework/blob/e40bc2436d2cf30302c69b79a171de10a441de38/Open%20UI%20Initiative%20Module%20Set.md) enumerates the list of modules and describes each of them at a high level. 
* An [**Open UI Module Specification**](https://github.com/NASWA-OpenUI/Open-UI-Framework/tree/e40bc2436d2cf30302c69b79a171de10a441de38/Module%20Documentation) defines how a given module will interact within a UI system, whether that is from one Open UI Module to another or from an Open UI Module to part of an existing UI system.
* An **Open UI Data Schema** (forthcoming) to support the standardized interactions specified for each module. 

### More details: [Open UI Module Specifications](https://github.com/NASWA-OpenUI/Open-UI-Framework/tree/e40bc2436d2cf30302c69b79a171de10a441de38/Module%20Documentation) 

#### Module Specifications: What’s in scope? 

The Open UI Framework is intended to capture UI system boundaries as individual module specifications. To do this, an Open UI Module specification will define:  
* Standardized format for data inputs and outputs; the specs will provide one or more examples in e.g., JSON or XML. 
* Application Programing Interface (API) specifications for how to trigger functionality within the module, including communication protocol and error handling.  
* Standardized data types, requests, and responses that the module will expose to the rest of the system. Some amount of data validation may also be standardized. 
* Configurable items as needed (whether that is defining certain variables to be set or enabling certain capabilities to be toggled on or off.) 

#### Module Specifications: What’s NOT in scope?  
The Open UI Framework is not intended to define specific implementation details for achieving functionality within a module. Therefore, an Open UI Module specification will **NOT**:  
* Define  business rules for achieving functionality within the module, as these are specific to each state’s UI program 
* Define the interfaces for how a module implementation would connect with external services to achieve the functionality within the module, although we will identify these where possible (e.g., how a module might use ICON to recieve necessary outputs) 
* Define the user interfaces for how the module functionality is achieved in an implementation as these will be state dependent and incorporate state-specific design patterns, branding, and other elements. 
* Define security/authentication requirements as these are unique to each state’s UI program and enterprise IT needs. 

### More details: Open UI Data Schema 

For Open UI Modules to be interoperable, we need a standardized data schema, or an outline of how the data should be organized in a database. With a standardized data schema, modules can exchange data without the need for third-party adapters. 

Each Open UI Module Spec does this within its own functional context (for example in defining inputs and outputs), but we will also create documentation in support of a clear data schema across the system. 

Where appropriate the Framework will also standardize field semantics as relates to, for example, how to handle company names that start with the word “The.” Doing this will clarify data handling across scenarios, whether that is within an Open UI module, among Open UI Modules, between an Open UI module and a non-standardized module, or between an Open UI Module and a central data infrastructure. 

<br>

## How to contribute to or support the Open UI Initiative

Find more information and updates on the Open UI Initiative at our [website](https://www.naswa.org/open-ui-initiative) or email us at [openui@naswa.org](mailto:openui@naswa.org).

If you have specific feedback to provide about content in the Framework Repository, such as feedback or a suggestion for a specific module specification, please see instructions for how to submit an Issue in our [Contributing Guide](https://github.com/NASWA-OpenUI/Open-UI-Framework/blob/e40bc2436d2cf30302c69b79a171de10a441de38/CONTRIBUTING.md).

Please review our [Code of Conduct](https://github.com/NASWA-OpenUI/Open-UI-Framework/blob/main/Contribution%20Guidelines/CODE_OF_CONDUCT.md) before submitting feedback.

