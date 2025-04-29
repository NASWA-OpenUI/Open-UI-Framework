# Federal Reporting Module

## Background
Federal reporting is a critical component of state unemployment insurance systems, requiring regular submission of standardized data to the U.S. Department of Labor (USDOL). These reports provide transparency, ensure compliance with federal requirements, and help track program performance across states.

Every state must submit various federal reports on specified schedules, with formats and content defined by USDOL. While reporting requirements are standardized, states have different processes for gathering, validating, and submitting this data.

## Definitions
A **federal report** is a standardized data submission that provides USDOL with information about a state's unemployment insurance program operations, including claims, payments, tax collection, and program performance. These reports typically follow defined formats with specific data elements and validation rules.

Key federal reports include:
- ETA 207 (Nonmonetary Determinations)
- ETA 218 (Benefit Rights and Experience)
- ETA 227 (Overpayment Detection/Recovery)
- ETA 581 (Contribution Operations)
- ETA 902 (UI Disaster Benefits)
- ETA 9056 (Appeals Time Lapse)

### Federal Reporting Module Scope
The Open UI Framework defines and standardizes how a Federal Reporting Module would collect data from and provide data to other parts of a UI system. This specification outlines the necessary inputs and outputs at a conceptual level, establishing the specific data formats for exchange with other modules.

### Inputs
What does the Federal Reporting Module need from other parts of a UI system?
- Claimant data (demographic information, benefits paid, eligibility determinations)
- Employer data (contributions, account statuses, employment data)
- Benefit payment data (amounts, types, dates)
- Appeals data (numbers, dispositions, timeliness)
- Overpayment and fraud data (detections, recoveries, prosecutions)
- Program performance data (timeliness metrics, quality measures)

### Outputs
What does the Federal Reporting Module provide to other parts of the UI system?
- Validation results for data used in federal reports
- Federal report submission status and history
- Performance dashboard data based on federal metrics
- Submission confirmations from federal systems
- Error reports and correction needs

### Interactions with Other Modules
The Federal Reporting Module interacts with several other modules in the Open UI Framework:
- **Monetary Determination Module**
  - Receives data on monetary determinations for claimants
  - Obtains information on established benefit years and weekly benefit amounts for ETA 218
- **Non-Monetary Determinations Module**
  - Receives data on separation issues, non-separation issues, and determination dispositions for ETA 207
- **Payments Module**
  - Receives data on benefit payments for claims across all programs
  - Obtains final payment information for calculating exhaustion rates
- **Appeals Module**
  - Receives data on lower and higher authority appeals volumes and dispositions
  - Obtains timeliness metrics for appeals processing for ETA 9056
- **Overpayment and Fraud Module**
  - Receives data on detected overpayments and fraud cases
  - Obtains recovery information for ETA 227
- **Tax Module**
  - Receives employer contribution data for ETA 581
  - Obtains employer status information

## Success Metrics
The following metrics will define success for the Federal Reporting Module:
- The module shall accurately aggregate data from source systems for all required federal reports
- The module shall validate data according to USDOL requirements prior to submission
- The module shall generate reports in the required formats and submit them by federal deadlines
- The module shall maintain an auditable history of all federal report submissions
- The module shall provide dashboards showing state performance on key federal metrics

## Conditions Necessary for Adoption
The Federal Reporting Module has significant dependencies on other modules for data inputs. For successful adoption:
- Source data systems must capture all required federal reporting elements
- Data quality protocols must be in place to ensure accuracy of reported information
- The module must be able to convert state-specific data structures into standardized federal formats
- While the module could be implemented independently of others, its value depends on reliable data connections to source systems

## Sources
- USDOL Unemployment Insurance Reports Handbook
- ETA 207, 218, 227, 581, 902, and 9056 reporting instructions
- Core Measures documentation
- UI SQSP (State Quality Service Plan) guidance
