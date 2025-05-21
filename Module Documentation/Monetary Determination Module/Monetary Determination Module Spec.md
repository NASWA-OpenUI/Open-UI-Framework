# Monetary Determination 

## Background
Monetary determination is a key part of whether an Unemployment Insurance (UI) claimant receives benefits. Beyond the monetary determination, a potential UI claimant must meet the other requirements of the UI program to receive benefits. 

A monetary determination can be made at multiple points in the lifecycle of a UI claim. For all UI claims, it is made after the claim is initially filed. For some UI claims, a “redetermination” to adjust an existing monetary determination might be necessary if an error of some kind was identified.  

Each state has their own process and formula for monetary determination based on their state’s laws, rules, and regulations, as well as their Unemployment Insurance agency’s interpretation of Federal laws, rules, and regulations. However, all states use the same kind of data and variables to make the determination. 

## Definitions 
A **monetary determination**, sometimes referred to as a **monetary entitlement**, is a set of calculations and decisions about whether a UI (Unemployment Insurance) claimant has earned sufficient wages in a period of time known as a **base period** to qualify for UI benefits. If there are sufficient wages in the base period, the monetary determination establishes a benefit year with a start and end date for when that claim is active for a claimant to receive benefits. The monetary determination also establishes: 
- The **maximum payable amount**, also known as the **maximum benefit entitlement**, which is the maximum amount a claimant may receive over the lifecycle of that claim,
- and the **weekly benefit amount**, which is the maximum amount the claimant may receive in a given week. 

The determination may also include more information about the claimant’s **work history**, i.e., wages earned for how many hours worked at which employer(s), to establish the monetary determination. 

### Monetary Determination Module Scope
The Open UI Framework defines and standardizes how a Monetary Determination Module would provide data to and get data from other parts of a UI system. In this version of the spec, we outline what we believe to be the necessary inputs and outputs of the module at a conceptual level, and the forthcoming module specification will establish the specific format for data inputs and outputs, as described in [What is the Open UI Framework](https://github.com/NASWA-OpenUI/Open-UI-Framework/blob/995812db30afba16cddb69d4f626c807b12e8093/README.md).
> As we work on the Monetary Determination Module Specification and others, and as we collaborate with and get feedback from the Open UI Community, the  scope of the modules and how we talk about them will likely change. 

### Inputs
What does the Monetary Determination Module need from other parts of a UI system to achieve its core functions? 
- Data about the UI claimant (unique identifier, name, address) 
- Claim start date 
- Wage and hour information by quarter from any employers that the claimant worked at during the base period, excluding any wages already “used” on another claim 
- Data about the employer(s) in which those wages/hours were worked (e.g., FEIN, name, address)

### Outputs
What does the monetary determination module need to provide for other parts of a UI system to use?  
- Base period used, both the relevant dates and the type of base period it was 
- What wages/hours were used to calculate the benefits in that claim, and whether there was any cancellation of wage credits 
- Which employer(s) is or are liable or responsible for the benefits in that claim 
- Weekly benefit amount 
- Maximum payable amount 
- Benefit year, whether a date range or separate start date and end date fields 
- Date of determination

### Interactions with Other Modules
When thinking about the scope of the Monetary Determination Module and defining its inputs and outputs, it’s helpful to think more specifically about the other modules within the [Open UI Module Set](https://github.com/NASWA-OpenUI/Open-UI-Framework/blob/995812db30afba16cddb69d4f626c807b12e8093/Open%20UI%20Initiative%20Module%20Set.md) that it will need to interact with. The other modules listed in this section are reflective of that list.

These interactions with other modules will also be codified as APIs in the forthcoming module specifications, as described in [What is the Open UI Framework](https://github.com/NASWA-OpenUI/Open-UI-Framework/blob/995812db30afba16cddb69d4f626c807b12e8093/README.md), but this module spec describes some of those interactions conceptually: 
- **Payments Module**
  - The Weekly Benefit Amount is the base from which any reductions or diversions are made to calculate how much a claimant will receive in a given benefit week.
  - The Payment Record will need to be cross referenced with the Maximum Payable Amount to ensure that the claimant isn’t receiving more than they are eligible for 
  - Overpayments may need to be created if the monetary determination is adjusted downward 
  - Underpayments may need to be created if the monetary determination is adjusted upward
- **Correspondence Module**
  - Monetary Determination Notices to the claimant will need to display key information output by the monetary determination module, such as the Maximum Payable Amount
  - Monetary Determination Notices to the liable/responsible employers will need to display key information output by the monetary determination module, such as the Maximum Payable Amount
- **Initial Claim Module**
  - The Claim Start date is needed for the Mondetary Determination Module to know what quarters' wages to retrieve
- **Federal Reporting**
  - Per [ETA 218](https://oui.doleta.gov/dmstree/handbooks/401/i_5.pdf), for specific time periods and claim types, the Federal Reporting Module will need to know the:
    - Total number of monetary determinations
    - Number of monetary determinations with sufficient wages
    - Number of monetary determinations with insufficient wages
    - Total number of claimants establishing benefit years
    - Number of claimants establishing benefits years that are entitled to the maximum Weekly Benefit Amount
    - Number of claimants establishing benefits years that are entitled to the maximum Weekly Benefit Amount and maximum duration of benefits
  - Per [ETA 207](https://oui.doleta.gov/dmstree/handbooks/401/i_4.pdf)
    - Total number of determinations and redeterminations
    - Number of determinations and redeterminations under the state’s UI program, additionally broken down by single- and multi-claimant totals
    - Number of determinations and redeterminations under UCX
    - Number of determinations and redeterminations under UCFE
- **State-specific Reporting**
- **Non-Monetary Determinations and Adjudications Module**
  - When a monetary determination has been made identifying a claim as monetarily eligible or qualified, the Non-Monetary Determinations and Adjudications Module will begin the process of making a non-monetary determination
- **Weekly Certification**
  - A Weekly Certification Module will need to know the Benefit Year as part of the check to know whether a claimant can file for benefits in a given week
  - An implemented Weekly Certification Module may want to show the claimant how much their Weekly Benefit Amount is
- **Wage Reporting**
  - The wage and hour records are needed to calculate the Maximum Payable Amount and Weekly Benefit Amount
- **Manage tax audit and Investigation Activities**
  - If a wage investigation is conducted and new wages are used or existing wages disqualified, a monetary redetermination will need to be made
  - Auditors will need to view the history of a claim’s monetary determination process
- **Appeals**
  -  A decision from a claimant or employer appeal could trigger the need to adjust the monetary determination

## Success Metrics
We will define success for the following metrics: 
- The monetary determination module shall accurately calculate reported wages to determine entitlement to UI benefits.
- The monetary determination module shall accurately calculate reported wages to determine maximum benefit entitlement.
- The monetary determination module shall accurately calculate reported wages to determine the weekly benefit amount.

## Conditions Necessary for Adoption
In addition to what is generally true of modules within the Open UI Framework, as described in [What is the Open UI Framework](https://github.com/NASWA-OpenUI/Open-UI-Framework/blob/995812db30afba16cddb69d4f626c807b12e8093/README.md), we believe it is unlikely that this module would be adopted on its own. However, once implemented, the Monetary Determination module could be able to be updated and/or replaced individually. More research is needed. 

## Sources
- [ETA State Comparison Guide](https://oui.doleta.gov/unemploy/pdf/uilawcompar/2023/monetary.pdf)
- [Chapter 3 Monetary Entitlement](https://oui.doleta.gov/unemploy/pdf/uilawcompar/2021/monetary.pdf)
- [Core Measures](https://oui.doleta.gov/unemploy/pdf/Core_Measures.pdf)
- [ETA Handbook #384](https://www.dol.gov/agencies/eta/advisories/handbooks/et-handbook-no-384)
- [ETA Handbook #391](https://www.dol.gov/agencies/eta/advisories/handbooks/et-handbook-no-391)
- [ETA Handbook #392](https://www.dol.gov/agencies/eta/advisories/handbooks/et-handbook-no-392)
- [ETA Handbook #395](https://www.dol.gov/agencies/eta/advisories/handbooks/et-handbook-no-395)
- [ETA Handbook #399](https://www.dol.gov/agencies/eta/advisories/handbooks/et-handbook-no-399)
- [Standard for Claim Determination—Separation Information](https://www.ecfr.gov/current/title-20/chapter-V/part-614/appendix-Appendix%20B%20to%20Part%20614)
- [Standard for Claim Filing, Claimant Reporting, Job Finding, and Employment Services](https://www.ecfr.gov/current/title-20/chapter-V/part-614/appendix-Appendix%20A%20to%20Part%20614)
