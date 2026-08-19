# Power Apps — IT Support Request Manager

## Overview

A Microsoft Power Apps application was created and published to provide a simplified interface for managing the **IT Support Requests** SharePoint list.

The application allows IT technicians to interact with support tickets without having to manage records directly from the SharePoint list.

## Application

**Name:** IT Support Request Manager

**Data Source:** SharePoint Online — IT Support Requests

## Application Features

The application allows technicians to:

* View existing IT support requests
* Search support tickets
* Create new tickets
* Edit existing tickets
* Assign technicians
* Update ticket priority and status
* Enter resolution notes
* Record resolution dates
* Review ticket descriptions and requester information

## SharePoint Integration

The Power App uses the existing **IT Support Requests** SharePoint list as its data source.

```text
Power Apps
IT Support Request Manager
        │
        ▼
SharePoint Online
IT Support Requests
        │
        ├── Issue
        ├── Requester
        ├── Department
        ├── Category
        ├── Priority
        ├── Status
        ├── Assigned Technician
        ├── Description
        ├── Resolution Notes
        └── Date Resolved
```

Changes made through Power Apps are written back to the SharePoint list.

Because Power Automate also monitors this list, changes made through the application can trigger the automated support workflows.

---

# Ticket Creation

The application was tested by creating a simulated **Software Installation Request**.

The ticket included:

* Requester: Amanda Taylor
* Department: Sales
* Category: Software
* Priority: Medium
* Status: New
* Assigned Technician: Stefon Kreller
* Description of the requested software installation

After saving the form, the new support request appeared in the ticket system.

### New Ticket Form

![New Ticket Form](../screenshots/power-apps/01-new-ticket-form.png)

### Saved Ticket

![Saved Ticket](../screenshots/power-apps/04-new-ticket-saved.png)

---

# Ticket Resolution

The application was also tested with a resolved **Microsoft 365 Application Access** support request.

The resolved ticket displayed:

* Status: Resolved
* Assigned Technician
* Resolution Notes
* Date Resolved

This demonstrated that technicians could maintain the complete support-ticket lifecycle from within Power Apps.

### Resolved Ticket

![Resolved Ticket](../screenshots/power-apps/02-resolved-ticket-details.png)

---

# Ticket Dashboard

The application provides a centralized interface for browsing support requests and viewing ticket details.

### Screenshot

![Ticket Dashboard](../screenshots/power-apps/03-ticket-dashboard.png)

---

# Power Apps Troubleshooting

## SharePoint Person Fields

During initial testing, the **Requester** and **Assigned Technician** fields displayed SharePoint claims values rather than readable user names.

An example claims value appeared similar to:

```text
i:0#.f|membership|user@tenant.onmicrosoft.com
```

The Person-field Combo Box controls were updated to use:

```text
Primary text: DisplayName
Search field: DisplayName
```

After the change, the application displayed readable names such as:

```text
Emily Brown
Stefon Kreller
```

instead of membership claims strings.

---

# Date Resolved Field

During testing, unresolved tickets displayed an incorrect default date of:

```text
12/31/2001
```

The Date Resolved control was adjusted so an unresolved ticket does not display a false resolution date.

When an actual resolution date exists, the stored date continues to display normally.

This resulted in a cleaner interface while preserving the ability to record resolution dates.

---

# Integration with Power Automate

Power Apps and Power Automate operate against the same SharePoint data source.

```text
Technician
    │
    ▼
Power Apps
    │
    ▼
IT Support Requests
SharePoint List
    │
    ├────────► New Ticket Notification
    │
    ├────────► High Priority Escalation
    │
    └────────► Resolution Notification
```

For example, when a technician updates a ticket to **Resolved** through the application, the SharePoint record is updated.

The Power Automate Ticket Status Notification workflow can then detect the change and notify the requester.

---

# Application Testing

The application was tested to verify:

* Existing tickets could be viewed
* Person fields displayed readable names
* New support requests could be entered
* Tickets could be saved to the SharePoint data source
* Existing tickets could be updated
* Resolution information could be displayed
* Unresolved tickets did not display an incorrect resolution date

---

# Application Publication

After configuration and testing were completed, the **IT Support Request Manager** application was saved and published.

Publishing the application created a finalized version of the support interface for the lab environment.

---

# Skills Demonstrated

* Microsoft Power Apps
* Canvas Apps
* SharePoint Integration
* Microsoft Lists
* Form Customization
* Data Cards
* Combo Box Controls
* Person Fields
* Power Fx
* Data Validation
* Ticket Management
* Application Testing
* Application Publishing
* Power Automate Integration
* Microsoft 365 Support
* Troubleshooting
* Technical Documentation

---

# Result

The IT Support Request Manager provides a functional front end for the SharePoint support-ticket system.

Together, the components create an integrated support solution:

```text
Power Apps
Ticket Interface
      │
      ▼
SharePoint
Ticket Data
      │
      ▼
Power Automate
Workflow Processing
      │
      ▼
Outlook
Notifications
```

This demonstrates how Microsoft Power Platform services can be combined with SharePoint Online to create a practical IT support workflow.
