# Power Automate Workflows

## Overview

Three Power Automate workflows were created to automate common IT support processes using the **IT Support Requests** SharePoint list.

The workflows demonstrate automated notifications, conditional escalation, ticket-status monitoring, dynamic SharePoint data, Outlook integration, and troubleshooting failed automation runs.

---

# Flow 01 — Support Request Notification

## Objective

Automatically notify the assigned technician whenever a new IT support request is submitted.

## Trigger

**SharePoint — When an item is created**

Data source:

**IT Support Requests**

## Action

**Office 365 Outlook — Send an email (V2)**

The recipient is dynamically retrieved from the ticket's **Assigned Technician Email** property.

The notification includes:

* Issue
* Requester
* Department
* Category
* Priority
* Status
* Description

## Workflow

```text
New SharePoint Ticket
        │
        ▼
When an item is created
        │
        ▼
Retrieve ticket information
        │
        ▼
Send email to Assigned Technician
```

## Troubleshooting

During initial testing, the email action failed because the SharePoint Person field returned a membership claims value instead of a standard email address.

Example:

```text
i:0#.f|membership|user@tenant.onmicrosoft.com
```

The flow was corrected by replacing the original Assigned Technician dynamic value with the **Assigned Technician Email** property.

After the correction, the flow was resubmitted successfully and the technician received the expected Outlook notification.

## Evidence

Screenshots are stored in:

```text
screenshots/power-automate/01-support-request-notification/
```

---

# Flow 02 — High Priority Ticket Escalation

## Objective

Automatically escalate newly submitted IT support requests when their priority is **High**.

## Trigger

**SharePoint — When an item is created**

## Condition

```text
Priority Value = High
```

## True Branch

If the condition evaluates to True, Power Automate sends a high-priority escalation email.

The email includes:

* Issue
* Requester
* Department
* Category
* Priority
* Assigned Technician
* Description

## False Branch

If the ticket does not have High priority, no escalation email is sent.

## Workflow

```text
New SharePoint Ticket
        │
        ▼
Check Priority
        │
        ▼
Is Priority = High?
      /             \
    Yes              No
     │                │
     ▼                ▼
Send Escalation    No escalation
Email
```

## Testing

A simulated ticket named **Finance Department Network Outage** was created with:

* Department: Finance
* Category: Network
* Priority: High
* Status: New

Power Automate evaluated the condition as True and successfully delivered the high-priority escalation email.

## Troubleshooting

During an earlier test, the condition completed successfully but the email action was skipped because the condition evaluated to False.

The condition was reviewed and corrected to use the SharePoint **Priority Value** dynamic content.

A new High-priority ticket was then submitted and the workflow successfully followed the True branch.

## Evidence

Screenshots are stored in:

```text
screenshots/power-automate/02-high-priority-escalation/
```

---

# Flow 03 — Ticket Status Notification

## Objective

Notify the requester automatically when an existing support ticket reaches **Resolved** status.

## Trigger

**SharePoint — When an item is created or modified**

## Condition

```text
Status Value = Resolved
```

## True Branch

When the ticket status equals Resolved, Power Automate sends an email to the **Requester Email** address.

The notification includes:

* Issue
* Status
* Assigned Technician
* Resolution Notes
* Date Resolved

## False Branch

Tickets that have not reached Resolved status do not receive the resolution notification.

## Workflow

```text
SharePoint Ticket Modified
        │
        ▼
Check Ticket Status
        │
        ▼
Is Status = Resolved?
      /               \
    Yes                No
     │                  │
     ▼                  ▼
Send Resolution     No notification
Notification
```

## Testing

The **Microsoft 365 Application Access** support request was updated to Resolved.

Resolution information was added documenting that the user's Microsoft 365 license assignment was verified and application access was restored.

The workflow ran successfully and generated an Outlook resolution notification containing the ticket status, technician, resolution notes, and completion date.

## Evidence

Screenshots are stored in:

```text
screenshots/power-automate/03-ticket-status-notification/
```

---

# Power Automate Architecture

```text
                     IT Support Requests
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
         New Ticket     High Priority   Ticket Updated
              │             │             │
              ▼             ▼             ▼
       Flow 01          Flow 02        Flow 03
              │             │             │
              ▼             ▼             ▼
       Technician       Escalation     Status Check
       Notification     Condition      Status=Resolved
              │             │             │
              ▼             ▼             ▼
            Outlook       Outlook       Outlook
```

---

# Skills Demonstrated

* Microsoft Power Automate
* Automated Cloud Flows
* SharePoint Triggers
* Conditional Logic
* Dynamic Content
* SharePoint Person Fields
* SharePoint Choice Fields
* Outlook Integration
* Automated Notifications
* Incident Escalation
* Ticket Lifecycle Automation
* Workflow Testing
* Failed-Run Analysis
* Root Cause Troubleshooting
* Microsoft 365 Support
* Technical Documentation

---

# Result

The three workflows created an automated ticket lifecycle around the SharePoint IT Support Requests list:

**New ticket → technician notification**

**High-priority ticket → automatic escalation**

**Resolved ticket → requester notification**

Together, these workflows demonstrate how Power Automate can reduce manual support tasks while providing consistent notifications throughout an IT support process.
