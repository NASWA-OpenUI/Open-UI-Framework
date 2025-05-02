# Weekly Certification

## Background
Weekly certification is a critical process in the Unemployment Insurance (UI) program that ensures continued eligibility for benefits after an initial claim has been approved. This process requires claimants to regularly verify that they continue to meet eligibility requirements to receive UI benefits. 

While monetary determination establishes initial eligibility and the potential benefit amounts, the weekly certification process confirms ongoing eligibility for each week a claimant seeks benefits. This ensures that UI benefits are only paid to individuals who remain eligible according to both federal and state requirements.

Each state has its own specific requirements and processes for weekly certification based on their state's laws, rules, and regulations, as well as their interpretation of Federal laws, rules, and regulations. However, all states collect similar types of information and ask similar questions as part of this process to determine continued eligibility.

User research shows that claimants often face challenges with the weekly certification process, including confusion about certification questions, difficulty remembering to certify on time, uncertainty about how to report earnings correctly, and trouble navigating certification systems. These challenges can lead to delayed payments, improper benefit determinations, and increased administrative workload for state agencies. A well-designed Weekly Certification Module addresses these challenges through user-centered design, clear communication, and appropriate reminders.

## Definitions
A **weekly certification** is the process by which UI claimants confirm their continued eligibility for benefits for a specific week. This involves answering a series of questions about their employment status, availability for work, job search activities, and any income earned during the claim week. The certification typically covers a **benefit week** (sometimes called a **claim week**), which in most states runs from Sunday to Saturday.

The weekly certification process verifies that a claimant:
- Remains unemployed or partially unemployed
- Is able and available for work
- Is actively searching for work (unless this requirement is waived)
- Has reported any earnings or other income for the week
- Has reported any job offers or refusals of work
- Has not violated any other eligibility requirements

Weekly certification questions typically include specific inquiries about:
- Physical ability and availability for work each day of the week
- Completion of qualifying work search activities
- Refusal of any job offers
- Receipt of workers' compensation
- Changes in retirement plans
- Holiday or vacation pay
- Severance or pay in lieu of notice
- Jury duty compensation
- Military Reserve or National Guard service
- Self-employment activity
- Any work performed (paid or unpaid)
- Receipt of sick pay

Successful completion of a weekly certification, along with meeting all eligibility criteria, results in a **benefit payment** for that week, up to the claimant's determined **weekly benefit amount**.

**Partial unemployment** refers to situations where claimants work reduced hours or part-time while receiving some unemployment benefits. The Weekly Certification Module must handle complex scenarios around partial employment, including proper classification of employment status and accurate calculation of partial benefits.

The most common **certification issues** that may require additional review or adjudication include:
- Work search compliance
- Able and available status
- School attendance
- Self-employment activity
- Separation issues (detailed classification of separation reasons)

### Weekly Certification Module Scope
The Open UI Framework defines and standardizes how a Weekly Certification Module would provide data to and get data from other parts of a UI system. In this version of the spec, we outline what we believe to be the necessary inputs and outputs of the module at a conceptual level. The forthcoming module specification will establish the specific format for data inputs and outputs.

### Inputs
What does the Weekly Certification Module need from other parts of a UI system to achieve its core functions?
- Claimant information (unique identifier, name, contact information)
- Claim information (benefit year begin/end dates, weekly benefit amount, maximum benefit amount, remaining balance)
- Work search requirements (number of required activities, any waivers or exemptions)
- Prior certification information (dates of previous certifications, previous responses)
- Any pending issues or holds on the claim
- Date range for the benefit week being certified
- State-specific parameters for certification questions (e.g., earnings disregard amounts)
- Payment method preferences
- Employment status information (including current part-time work status)
- Notification preferences (email, text, phone)
- Accessibility requirements for claimants with disabilities
- Information about scheduled holidays during the claim week
- Information about the claimant's separation reason and status (laid off, fired, quit, etc.)
- Military service information, if applicable
- School attendance or training program enrollment information

### Outputs
What does the Weekly Certification Module need to provide for other parts of a UI system to use?
- Certification status (completed, incomplete, pending verification)
- Claimant responses to certification questions, including:
  - Able and available status for each day of the claim week
  - Completed work search activities and documentation
  - Any job offers received or refused
  - Any workers' compensation applied for or received
  - Any changes in retirement plans or benefits
  - Any holiday or vacation pay received or to be received
  - Any severance pay or pay in lieu of notice
  - Any jury duty compensation
  - Any military reserve or National Guard service
  - Any self-employment activity
  - Any work performed for an employer (paid or unpaid)
  - Any sick pay received or to be received
- Work search activities reported (dates, employer contacts, other activities)
- Any reported earnings or other income for the week, with specific categorization
- Any reported job offers or refusals, with detailed reasons
- Any reported changes in circumstances that may affect eligibility
- Date and time of certification submission
- Method of certification (online, phone, etc.)
- Payment eligibility determination for the week
- Amount to be paid (if eligible), with any applicable deductions or offsets
- Potential issues requiring further review or adjudication, categorized by issue type
- Flags for common certification issues (work search, able and available, school attendance, self-employment, separation)
- Changes in employment status (from full employment to partial employment or vice versa)

### Interactions with Other Modules
When thinking about the scope of the Weekly Certification Module and defining its inputs and outputs, it's helpful to think more specifically about the other modules within the Open UI Module Set that it will need to interact with.

These interactions with other modules will be codified as APIs in the forthcoming module specifications, but this module spec describes some of those interactions conceptually:

- **Initial Claim Module**
  - Provides the foundational claim information needed for weekly certification, including benefit year dates, weekly benefit amount, and maximum benefit amount
  - May receive updates from Weekly Certification Module about potential eligibility issues identified during certification
  - Supplies separation reason information that may affect weekly certification requirements

- **Monetary Determination Module**
  - Provides the weekly benefit amount and maximum benefit amount that form the basis for payment calculations
  - Supplies information about any applicable partial benefit formula or earnings disregard for reporting work and earnings
  - Shares wage record information to help validate reported earnings during weekly certification

- **Payments Module**
  - Receives payment instructions from the Weekly Certification Module when a certification is approved
  - Provides payment history that may be needed during the certification process
  - Updates remaining balance information after payments are processed
  - Handles payment calculations for partial benefits when claimants report earnings
  - Processes direct deposit or debit card payments based on claimant preferences

- **Non-Monetary Determinations and Adjudications Module**
  - Receives information about potential eligibility issues identified during certification (e.g., job refusals)
  - Provides outcomes of adjudications that may affect future certifications
  - Informs Weekly Certification Module about any eligibility issues that would prevent payment
  - Processes information about the five most common certification issues:
    - Work search compliance
    - Able and available status
    - School attendance
    - Self-employment activity
    - Separation issues (including detailed classification of separation reasons)

- **Correspondence Module**
  - Generates notices to claimants about certification requirements, deadlines, and outcomes
  - Sends reminders about upcoming certification periods via preferred communication channels
  - Issues notifications about certification problems or missing information
  - Provides accessible communication options for claimants with disabilities
  - Delivers certification instructions in multiple languages as needed

- **Federal Reporting Module**
  - Receives certification and payment data needed for various federal reports
  - Weekly certification activity feeds into required reports like the ETA 5159 (Claims and Payment Activities)
  - Certification and payment outcomes contribute to performance metrics
  - Collects data on timeliness of certifications and payments

- **Wage Reporting/Crossmatch Module**
  - Provides verification of reported earnings through employer wage records
  - Identifies potential discrepancies between reported and actual earnings
  - Helps determine proper classification for partial employment status
  - Validates holiday, vacation, and severance pay information

- **Work Search Module**
  - Receives work search activities reported during certification
  - May provide validation of work search activities
  - Stores historical work search information
  - Calculates compliance with state-specific work search requirements
  - Flags potential work search issues for adjudication

- **Appeals Module**
  - Receives appeals related to certification denials
  - Provides information about appeal outcomes that may affect certification status
  - Records historical appeal information that may affect future certifications

- **Overpayments Module**
  - Receives information when certifications are retroactively determined ineligible
  - Provides information about existing overpayments that may affect payment amounts
  - Processes recoupment of overpayments from current benefit payments

- **Identity Verification Module**
  - Validates claimant identity for weekly certification submissions
  - Provides authentication mechanisms for online, phone, and other submission methods
  - Flags potential identity issues for fraud prevention

## Success Metrics
We will define success for the following metrics:
- The Weekly Certification Module shall accurately collect and process claimant certification information to determine eligibility for weekly benefit payments.
- The Weekly Certification Module shall correctly apply state-specific rules regarding earnings reporting, work search requirements, and other eligibility factors.
- The Weekly Certification Module shall efficiently identify potential eligibility issues requiring further review or adjudication.
- The Weekly Certification Module shall transmit accurate payment instructions to the Payments Module for eligible weeks.
- The Weekly Certification Module shall provide timely and clear information to claimants about certification requirements and outcomes.
- The Weekly Certification Module shall achieve a high rate of "First Time Completion" of weekly certifications.
- The Weekly Certification Module shall support "Timely Certifications" from claimants by providing clear reminders and intuitive interfaces.
- The Weekly Certification Module shall minimize the need for adjudication by providing clear questions and helpful guidance during the certification process.
- The Weekly Certification Module shall support accessible certification options for claimants with disabilities.
- The Weekly Certification Module shall provide appropriate language translation for non-English speakers.
- The Weekly Certification Module shall accurately calculate partial benefits for claimants with reported earnings.
- The Weekly Certification Module shall provide tools for claimants to accurately calculate and report all types of earnings and income.

## Conditions Necessary for Adoption
In addition to what is generally true of modules within the Open UI Framework, as described in Conditions Necessary for Adoption, we believe the Weekly Certification Module would be most effective when implemented alongside several other core modules, particularly:

- Initial Claims Module: Provides the foundational claim information
- Monetary Determination Module: Establishes benefit amounts and duration
- Payments Module: Processes payments based on certification outcomes
- Non-Monetary Determinations Module: Resolves eligibility issues

While it may be possible to implement the Weekly Certification Module independently with appropriate interfaces to existing systems, its full functionality depends on standardized data exchanges with these related modules.

### User Experience Considerations
Successful implementation of the Weekly Certification Module must also consider the following user experience factors:

#### For Claimants:
- Simple, plain language descriptions of certification processes and requirements
- Reminder notifications across all communication channels (email, text, phone)
- Translations into commonly spoken languages
- Calculators for accurately tallying work completed since the last certification
- Clear instructions for recertification after benefit year has ended
- Intuitive mobile-friendly interfaces that allow completion from any device
- Accessibility features for claimants with disabilities
- Guided explanations for confusing certification questions (e.g., ability to work, actively seeking work)
- Error messages that clearly explain how to fix issues

#### For Agency Staff:
- Simplified process for cross-checking claimant-supplied information with employer records
- Automated tools to identify potential discrepancies or fraud indicators
- Dashboard views of certification status for individual claims and aggregate monitoring
- Categorized issue flags to streamline adjudication workflows
- Reporting tools to track timely certification rates and payment timeliness

## Sources
- [ETA State Comparison Guide](https://oui.doleta.gov/unemploy/pdf/uilawcompar/2023/monetary.pdf)
- [UI Reporting Requirements](https://oui.doleta.gov/unemploy/DataDashboard.asp)
- [Department of Labor Weekly Certification Guidance](https://www.dol.gov/agencies/eta/ui-modernization/initial-application/weekly-certification)
- [ETA Handbook #384](https://www.dol.gov/agencies/eta/advisories/handbooks/et-handbook-no-384)
- [ETA Handbook #401](https://oui.doleta.gov/dmstree/handbooks/401/401_toc.asp)
- Washington State UI Weekly Certification Requirements (2024)
- Illinois IDES UI Claimant Portal and Application Personas and Journey Document (2024)
- State UI Weekly Claim Certification Questions (multiple states)
- [State Information Data Exchange System](https://edd.ca.gov/en/SIDES)
- [Open UI Initiative](https://www.dol.gov/agencies/eta/ui-modernization/open-UI-initiative)
