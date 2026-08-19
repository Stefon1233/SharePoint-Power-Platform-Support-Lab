# Ticket 04 — High Priority Network Outage

## Ticket Information

- **Requester:** Emily Brown
- **Department:** Finance
- **Category:** Network
- **Priority:** High
- **Assigned Technician:** Stefon Kreller
- **Status:** New

## Issue

The user reported loss of network connectivity and inability to access Microsoft 
365 services or shared company resources.

The issue was preventing normal business operations and required immediate 
investigation.

## Investigation

1. Reviewed the newly submitted support request.
2. Verified the issue was categorized as Network.
3. Confirmed the ticket Priority was set to High.
4. Verified the Power Automate High Priority Ticket Escalation workflow detected 
the new ticket.
5. Confirmed the Priority condition evaluated successfully.
6. Verified the True branch executed.
7. Confirmed the escalation email was delivered through Outlook.

## Automated Escalation

The Power Automate workflow evaluated:

`Priority Value = High`

Because the condition evaluated to True, the workflow automatically sent a 
high-priority escalation email.

The notification included:

- Issue
- Requester
- Department
- Category
- Priority
- Assigned Technician
- Description

## Result

The high-priority support request successfully triggered the automated 
escalation workflow.

The test demonstrated how conditional automation can identify urgent support 
requests and automatically notify IT personnel without requiring manual 
escalation.

## Automation Demonstrated

High Priority SharePoint Ticket  
→ Power Automate Trigger  
→ Priority Condition  
→ Priority = High  
→ True Branch  
→ Escalation Email Sent

## Technologies Used

- SharePoint Online
- Microsoft Power Automate
- Conditional Logic
- Microsoft Outlook
- Microsoft 365
- Incident Escalation
- Workflow Testing
