# Governance & Security

## Overview

Governance was incorporated into the IT support environment to demonstrate controlled access, centralized administration, permission management, and separation of responsibilities across Microsoft 365 and Power Platform services.

The lab uses SharePoint permissions, Microsoft Entra ID security groups, Power Apps, and Power Automate to create a structured support environment rather than granting unrestricted access directly to individual users.

---

## Group-Based Access Control

Technician access was managed through the Microsoft Entra ID security group:

`SG-IT-Support-Technicians-Security`

Members included:

- John Smith
- Kevin Brown
- Stefon Kreller

The group was granted **Edit** access to the SharePoint support environment.

This provides centralized access management:

```text
Technician
     │
     ▼
Entra ID Security Group
     │
     ▼
SharePoint Permission
     │
     ▼
IT Support Resources
```

Instead of granting permissions independently to every technician, administrators can manage access through group membership.

---

## Permission Levels

Different SharePoint permission levels were used to separate administrative and user access.

| Role | Permission Level | Purpose |
|---|---|---|
| Site Owners | Full Control | Administrative management |
| Site Members | Edit | Modify site content |
| Site Visitors | Read | View content without modification |
| IT Support Technicians | Edit | Manage support resources |

This demonstrates the principle of assigning permissions according to job responsibilities.

---

## Unique Permissions

The lab also demonstrated SharePoint permission inheritance and unique permissions.

Permission inheritance was reviewed before access was modified.

Unique permissions were then configured to demonstrate more granular control over SharePoint resources.

This included:

- Reviewing inherited permissions
- Breaking permission inheritance
- Removing unnecessary access
- Granting Read access
- Verifying the resulting permissions

These steps demonstrated how administrators can restrict access to sensitive resources without changing permissions across the entire SharePoint environment.

---

## Permission Verification

Permissions were not assumed to be working solely because they were assigned.

SharePoint's **Check Permissions** feature was used to verify effective access.

During testing, John Smith was confirmed to receive **Edit** permission through:

`SG-IT-Support-Technicians-Security`

This provided evidence that the group-based permission model was functioning correctly.

---

## Least-Privilege Approach

The lab applied least-privilege concepts by assigning users the level of access required for their responsibilities.

Examples included:

- Read access for users who only needed to view resources
- Edit access for technicians responsible for managing support resources
- Full Control reserved for administrative roles
- Security-group membership used instead of unnecessary individual permission assignments

The objective is to avoid granting more access than is required to perform a role.

---

## Centralized Identity Management

Microsoft Entra ID provides centralized identity and group management for the environment.

Technician access can be managed by modifying membership in the security group.

### Technician Onboarding

```text
Create/Enable User
       │
       ▼
Add User to Technician Security Group
       │
       ▼
User Receives Group-Based Access
```

### Technician Offboarding

```text
Remove User from Technician Security Group
       │
       ▼
Group-Based Access Removed
       │
       ▼
Review Remaining Access
```

This is more scalable than manually assigning the same permissions to every technician.

---

## SharePoint as the Controlled Data Source

The **IT Support Requests** SharePoint list serves as the central data source for the support-ticket solution.

Ticket information includes fields such as:

- Requester
- Department
- Category
- Priority
- Status
- Assigned Technician
- Description
- Resolution Notes
- Date Resolved

Power Apps and Power Automate interact with this centralized SharePoint data rather than maintaining separate ticket databases.

---

## Power Apps Governance

The **IT Support Request Manager** Power App provides an interface for working with support-ticket data stored in SharePoint.

The application does not replace SharePoint permissions.

Users still require appropriate access to the underlying data source.

This creates the following access relationship:

```text
User Identity
     │
     ▼
Entra ID
     │
     ▼
SharePoint Permission
     │
     ▼
Power Apps
     │
     ▼
IT Support Request Data
```

This demonstrates why application access and data-source access both need to be considered when administering Power Platform solutions.

---

## Power Automate Governance

Power Automate workflows were created to respond to ticket events in the SharePoint list.

The lab implemented workflows for:

1. New support request notification
2. High-priority ticket escalation
3. Resolved-ticket notification

These workflows use defined triggers, conditions, and actions rather than requiring technicians to manually send every notification.

Automation helps standardize the support process while maintaining SharePoint as the central source of ticket information.

---

## Administrative Separation

The environment demonstrates several layers of administration:

```text
Microsoft Entra ID
Identity & Security Groups
        │
        ▼
SharePoint Online
Data & Permissions
        │
        ▼
Power Apps
User Interface
        │
        ▼
Power Automate
Business Logic
        │
        ▼
Outlook
Notifications
```

Separating these responsibilities makes the environment easier to manage and troubleshoot.

For example, an access problem can be investigated by checking:

1. User identity
2. Security-group membership
3. SharePoint permissions
4. Power Apps data access
5. Workflow configuration

---

## Governance Practices Demonstrated

The lab demonstrates:

- Centralized identity management
- Security-group-based access
- SharePoint permission levels
- Permission inheritance
- Unique permissions
- Least-privilege concepts
- Effective permission verification
- Controlled access to support data
- Separation of administrative responsibilities
- Centralized ticket data
- Automated workflow processing
- Application and data-source access considerations
- Technician onboarding/offboarding concepts

---

## Skills Demonstrated

- Microsoft 365 Governance
- Microsoft Entra ID
- Identity and Access Management
- SharePoint Online Administration
- Security Groups
- Permission Management
- Least Privilege
- Access Control
- Power Apps Administration
- Power Automate Administration
- Microsoft 365 Security Concepts
- User Lifecycle Management
- Troubleshooting
- Technical Documentation

---

## Result

The support environment was configured with a structured access-control model rather than relying on unrestricted or individually managed access.

Microsoft Entra ID security groups provide centralized technician membership management, while SharePoint permission levels control access to the underlying support resources.

Power Apps provides the ticket-management interface and Power Automate handles workflow processing while continuing to rely on SharePoint as the central data source.

Together, these components demonstrate practical Microsoft 365 and Power Platform governance concepts within an IT support environment.