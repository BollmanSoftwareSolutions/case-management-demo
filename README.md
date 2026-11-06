# Fraud Case Management Demo
This is a back office case management application that provides bank employees a workflow to handle financial fraud.

**Customer** calls into their bank's help line to report a fraudulent transaction on one of their accounts.
**Fraud Specialist** records reported information (ex. date, amount, vendor, etc) and intiates and investigation. They may reach out to the customer for additional information based on system actions.
**Administrator** creates the workflows for different types of fraud cases.

## Running the demo
// TODO

## The Production Application
For descriptive purposes only. This README outlines the workflow and technology used for the Production application. The demo application will use other libraries and a simplified, client only UI.

# Technology
## Frontend Technology
This is a desktop application that runs on a bank employees authorized computer. The UI was built with WPF in C# using an MVVM pattern. Workflows are built in the UI with visual modelling as drag and drop components (like the Scratch programming process).

Workflow components (ex. send email, VISA query, etc) are populated using .NET DLLs hosted in the same application directory. DLLs are built with specific interfaces that expose an execution method to be triggered. Bank customers could use the product with built-in libraries as a COTS product or contract with the business to build custom workflow components.

## Frontend Tech List
- WPF
- C#
- .NET Framework 4.8

## Backend Technology
Each customer self-hosted an ASP.NET API with IIS and a Microsoft SQL database. Customers may have had other systems with which our application interfaced.

### Backend Tech List
- SQL
- ASP.NET REST API
- IIS

# Roles
## Customer
The bank customer that reports fraudulent transactions.

## Fraud Specialist
The bank employee that handles fraud reports and handles the workflow for an investigation. Many steps are automated but others may require decisions from the employee. They may contact the customer to solicit additional information.

## Administrator
The user that sets up the workflows using the visual modelling functionality.

# Access and Security
Applications used the bank's own authorization scheme, often their SSO system.

# Workflow
## Overview
// TODO

## Example workflow
// TODO: convert to diagram

[1 Case Creation] 

-> [2 Internal system lookup] 

-> [3 DECISION] IF is found -> [4 VISA query] -> [5 CONTACT VENDOR] ->

-> [3 DECISION] ELSE not found -> [3a CONTACT CUSTOMER] -> GO TO [2] 

-> [6 DECISION] IF Vendor disputes AND transaction < $50 -> [7 FINAL DECISION] Issue Refund

-> [6 DECISION] ELSE IF Vendor disputes AND transaction > $50 -> [7 FINAL DECISION] Deny Refund

-> [6 DECISION] ELSE IF Vendor confirms -> [8 DECISION] IF Transaction >= $1000 -> [9 CONTACT POLICE] 

-> [8 DECISION] ELSE transaction < $1000 -> [7 FINAL DECISION] Issue Refund -> 

## Steps
### Workflow Setup - Administrator
1. **Administrator** creates named workflow
2. **Administrator** selects workflow actions and decision points
    - Can create IF-ELSE flows that separate workflows (ex. transaction dollar value)
3. **Administrator** selects other named workflows that can be reused
    - Reusable Workflow fragments may be things like transaction look ups, templated emails, etc.
4. **Administrator** publishes workflow for use by **Fraud Specialist**.

### Case Initiation
1. **Customer** calls or submits an online notice
2. **Fraud Specialist** enters the relevant information into the case creation form.
    - **Fraud Specialist** contacts customer for additional information if needed.

### Investigation
1. The system begins the automated workflow when the case is created.
2. System looks up transaction information, sends notifications, queries VISA or other payment processor.
3. System stops processing and notifies user when a decision must be made.
    - Workflows can split based on specific criteria (ex. transactions > $500 have a different flow than transactions < $500)

### Final Decision
1. System notifies **Fraud Specialist** of system recommendation.
2. **Fraud Specialist** decides next action
    - System sends notification of decision to customer
    - OR escalates case for further review.
