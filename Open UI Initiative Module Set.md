# Open UI Initiative Module Set V0.1

## Status: Work in Progress 

Based on our research to date, this document outlines what we believe the Open UI Module Set should include. We recognize this will be an iterative process—refining our approach through direct feedback on this document, validating assumptions as we explore technical specifications, and adjusting as we move into prototyping or pilot testing.

## Background 

A module, in the context of software or system architecture, is a self-contained unit that encapsulates one or more related functionalities or services. Modules serve as cohesive building blocks within a larger system, providing a level of orchestration and organization that enhances manageability, reusability, and scalability. 

The encapsulation allows the module to be developed, tested, and maintained independently from other parts of the system. Modules can vary in size and complexity, ranging from small, single-purpose components to larger, multi-functional entities. 

The complete Open UI Module Set is the minimum set of bounded functionalities (modules) needed to fully support the administration of Unemployment Insurance. The set seeks to minimize the overlap of functionality between the modules and maximize coverage of the functions required to administer and deliver unemployment insurance programs. 

## Considerations for Defining Open UI Modules 

As we define Open UI Modules, there are many parts of administering UI programs that the specifications will need to consider, such as: 
* Issue Detection: This can occur at nearly any point in the system and typically initiates fact-finding and decision-making processes when necessary.
* Federal reviews and corresponding quality checks 
* Workflow Engine: More research is needed to better define the relationship between functionality within modules and overall workflows, both automatic and manual, that keep a UI system running.  
* User Interfaces: While we know that the Open UI Framework is not going to define or specify user interfaces, there is more that we need to do in terms of understanding and documenting the relationship between the functionality within modules, the users involved in that functionality, and the way that those users interact with that functionality. 

## The List of Open UI Modules 

### High confidence: Modules that Open UI has confidence are necessary with clearly defined, well-understood boundaries

**Account Management:** The Account Management module includes functionality for user account creation and maintenance. This includes self-service and staff-assisted account management for claimants and employers and administrative user access management for staff user accounts. This includes managing users' profiles. 

**Initial Claim:** This module supports the collection of comprehensive information to file an initial unemployment insurance claim for standard Unemployment Compensation (UC), UC for Federal Employees (UCFE), and UC for Ex-Servicemembers. The data required includes claimant's employment history, current ability and availability to work, and reasons for job separation at the time of filing. The Initial Claims Module is the source of truth for the claim record.  

**Federal Reporting Module:** This module includes functionality to generate and manage all reports required byt the U.S. Department of Labor (USDOL/ETA). 

**Monetary Determination:** The Monetary Determination module enables a set of calculations and decisions to assess monetary eligibility, including the establishment of a benefit year, weekly benefit amount, and maximum payable amount. This module includes determining potential benefit liabilities for each employer, including noncharging and payment reductions.  

**Non-Monetary Determination:** The Non-Monetary Determination module is used to gather and review fact-finding information regarding potential barriers to unemployment eligibility at the claim level, including (but not limited to) the claimant’s reason for separating from their job, their availability and ability to work, and whether they are actively seeking work. This module covers the setting and resolution of non-monetary issues, including redeterminations. 

**Payments:** The Payments module includes functionality to process accurate payments issued by multiple payment methods, manage tax and child support withholding and make payment adjustments. The Payments Module also contributes to the source of truth for the payment record.  

**Weekly Certification:** The Weekly Certification module focuses on gathering the data needed for ongoing eligibility during a claim’s benefit year, including the setting and resolution of issues related to these data. 

### Lower confidence: More research is needed before modules boundaries are defined 

**Appeals:** The Appeals module includes functionality for all appeal levels (as determined by state statute and regulations) for appeals from both claimants and employers. This module covers appeals filed on benefit claims, as well as appeals by employers regarding employer liability, classification of workers and tax rates. It is possible that this will break down into multiple modules. 

**Benefits Program Integrity:** The module includes functionality to prevent, detect, and manage improper payments. It also includes the means to process and manage overpayments (establishing, determining interest/penalties, etc.). More research is needed to understand the correct modular granularity. 

**Cashiering and Accounting:** The Cashiering and Accounting Transactions module includes the acceptance and processing of employer payments (from both contributory and reimbursement employers) via multiple payment methods. This includes all managing activities such as applying payments within the established rules of priority, posting the payments, managing dishonored payments, reversing, and transferring payments, and processing payment file data for account reconciliation. 

**Collections:** The Collections module includes the means to process and manage overpayments and collecting debts. Rather than be a standalone module, it may be incorporated into one of the other modules described above. 

**Correspondence:** This module will create messaging, documents, and information for both claimants and employers and manage the dissemination methods. This merits more investigation and may be broken down into smaller modules, though we have high confidence in the need for the creation of correspondence to multiple different user groups. 

**Document Management:** The Document Management module includes functionality related to the scanning, upload, storage, and retrieval of documents by claimants, employers, and staff. It is likely to be a commoditized tools with inputs coming from the Open UI Framework. 

**Federal Certification:** The Federal Certification module includes the functionality for staff to process and create Federal Unemployment Tax Act (FUTA) identification files, and process the FUTA Update file, as well as self-service and staff-assisted requests for FUTA 940 Re-Certifications. 

**Liability Type:** The Liability Type module includes functionality to gather business registration information to determine the employer’s liability to pay unemployment insurance taxes/contributions. Also included is the functionality to update employer account information, including account closure and business transfers. 

**Manage Employer Receivables and Delinquencies:** This module includes functionality to manage assessments, determine collectible receivables, manage delinquencies, interest, penalties adjustments, bankruptcies, and multiple available collections methods. 

**Performance and Quality Activities:** There are many USDOL/ETA mandated audits (e.g., BAM, BTQ, and Appeals)  as well as internal audits for performance related activities. It also needs to account for the functionality of the Tax Performance System (TPS) and SUTA Dumping activities. Some may be individual modules and some may be processes that the modules support.  

**State-specific Reporting Module:** State-specific operations reports may be a separate module or included in the overall Reporting Module; more research is needed on the similarities across states. 

**Tax Audit and Investigation Activities:** The Manage Audit / Investigation Activities module includes functionality pertinent to the management, assignment, and completion of tax field audit activities for multiple audit and investigation types. 

**Tax Integrity/Fraud:** The Integrity/Fraud module includes functionality to prevent, detect, and manage such things as misclassification, fraudulent accounts, unreported wages, and SUTA dumping activities, through crossmatching other means. 

**UI Experience Tax Rate:** The UI Experience Tax Rate module includes the functionality to determine the experience rating history and calculate employer tax rates upon registration, for the annual rate run, and upon requirement to recalculate. It also includes the ability to manage partial rate transfers and joint/group rates. 

**Wage and Tax Data:** The Wage and Tax Data module enables submission of tax and wage reports, as well as wage corrections and scheduled payments.  

**UI Trust Fund Accounting:** The Unemployment Trust Fund Accounting module includes functionality necessary to manage and reconcile the Unemployment Trust Fund, including transfer and management of penalty and interest (P&I) funds. 
