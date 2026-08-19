# SharePoint IT Support Requests List

## Overview

A SharePoint Online list named **IT Support Requests** was created to serve as the central data source for the IT support workflow.

The list stores support-ticket information used by SharePoint, Power Apps, and Power Automate.

## List Configuration

The following fields were configured:

| Field               | Purpose                                  |
| ------------------- | ---------------------------------------- |
| Issue               | Identifies the support problem           |
| Requester           | User requesting assistance               |
| Department          | Requester's business department          |
| Category            | Type of support request                  |
| Priority            | Determines ticket urgency                |
| Status              | Tracks ticket progress                   |
| Assigned Technician | Technician responsible for the request   |
| Description         | Detailed description of the issue        |
| Resolution Notes    | Documents troubleshooting and resolution |
| Date Resolved       | Records when the ticket was completed    |

## Categories

Support requests can be classified as:

* Account Access
* Microsoft 365
* Hardware
* Software
* Network
* Other

## Priority Levels

* Low
* Medium
* High
* Critical

Priority information is also used by Power Automate to determine whether a ticket requires automatic escalation.

## Ticket Statuses

* New
* In Progress
* Waiting on User
* Resolved
* Closed

Ticket status information is used by Power Automate to determine when resolution notifications should be sent.

## Example Support Requests

The list was populated with simulated incidents including:

* SharePoint Access Denied
* Microsoft 365 Application Access
* Power Automate Notification Failure
* VPN Connection Failure
* Finance Department Network Outage
* Software Installation Request

These tickets provided test data for the Power Apps application and Power Automate workflows.

## Integration

The SharePoint list serves as the central data source for the lab.

```text
IT Support Requests
        │
        ├── Power Apps
        │     └── Ticket management interface
        │
        └── Power Automate
              ├── New ticket notification
              ├── High-priority escalation
              └── Resolution notification
```

Creating or modifying SharePoint items can therefore trigger automated actions while Power Apps provides a separate interface for technicians to interact with the same underlying ticket data.

## Screenshot

![IT Support Requests List](../screenshots/sharepoint/01-it-support-requests-list.png)

## Skills Demonstrated

* SharePoint Online
* SharePoint Lists
* Microsoft Lists
* Data organization
* Choice columns
* Person columns
* Microsoft Power Platform integration
* IT ticket management
* Technical documentation
