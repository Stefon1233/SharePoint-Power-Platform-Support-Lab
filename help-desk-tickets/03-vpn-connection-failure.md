# Ticket 03 — VPN Connection Failure

## Ticket Information

- **Requester:** Jessica Miller
- **Department:** HR
- **Category:** Network
- **Priority:** High
- **Assigned Technician:** Stefon Kreller
- **Status:** New

## Issue

The user reported being unable to connect to the company VPN and receiving a 
connection error.

The issue prevented the user from accessing network resources required for 
normal work activities.

## Investigation

1. Reviewed the support request submitted through the IT Support Requests 
system.
2. Verified the ticket was categorized as a Network issue.
3. Reviewed the ticket priority and assigned technician.
4. Confirmed the SharePoint ticket was successfully detected by Power Automate.
5. Reviewed the automated technician-notification workflow.

## Automation Troubleshooting

During testing, the Power Automate email action initially failed.

The SharePoint Assigned Technician Person field returned a membership claims 
value instead of a standard email address.

The workflow was corrected by using the **Assigned Technician Email** dynamic 
property.

The failed run was then resubmitted successfully.

## Resolution

The Power Automate support-request notification workflow was corrected and 
successfully delivered the VPN support-request notification to the assigned 
technician.

The ticket demonstrated both IT incident tracking and Power Automate workflow 
troubleshooting.

## Automation Demonstrated

New SharePoint Ticket  
→ Power Automate Trigger  
→ Assigned Technician Email Retrieved  
→ Outlook Notification Sent

## Technologies Used

- SharePoint Online
- Microsoft Power Automate
- Microsoft Outlook
- SharePoint Person Fields
- Microsoft 365
- Workflow Troubleshooting
