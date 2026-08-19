# SharePoint Permissions and Access Control

## Overview

This portion of the lab demonstrates SharePoint permission inheritance, unique list permissions, direct user access, permission verification, and the principle of least privilege.

The **IT Support Requests** list initially inherited permissions from its parent SharePoint site. The permissions were then customized to better restrict access to IT support information.

---

## Initial Permission Configuration

The IT Support Requests list initially inherited permissions from its parent SharePoint site.

The inherited configuration included:

* **IT Knowledge Base Owners** — Full Control
* **Members** — Edit
* **Visitors** — Read

This meant users with access to the parent site could automatically receive access to the support-request list.

### Screenshot

![Inherited Permissions](../screenshots/permissions/01-inherited-permissions-before.png)

---

## Breaking Permission Inheritance

Permission inheritance was disabled for the IT Support Requests list.

This created **unique permissions**, allowing access to the support list to be managed independently from the parent SharePoint site.

Existing permissions were initially copied to the list when inheritance was stopped.

### Screenshot

![Unique Permissions](../screenshots/permissions/02-unique-permissions-after.png)

---

## Removing Visitor Access

The Visitors group was removed from the IT Support Requests list.

This prevented users who only required general read access to the parent site from automatically receiving access to support-ticket information.

Owners and authorized members retained their existing access.

### Screenshot

![Visitor Access Removed](../screenshots/permissions/03-visitors-access-removed.png)

---

## Least-Privilege User Access

A test user, **Emily Brown**, was granted direct **Read** access to the IT Support Requests list.

This demonstrated how an individual user can receive access without being granted unnecessary Edit or Full Control permissions.

The resulting access model demonstrated multiple permission levels:

| User/Group               | Permission   |
| ------------------------ | ------------ |
| IT Knowledge Base Owners | Full Control |
| Authorized Members       | Edit         |
| Emily Brown              | Read         |

### Screenshot

![Read Access Granted](../screenshots/permissions/04-user-read-access-granted.png)

---

## Permission Verification

SharePoint's **Check Permissions** feature was used to verify the test user's effective permissions.

The verification confirmed that Emily Brown received:

**Read — Given directly**

This demonstrated that the permission assignment was functioning as intended.

### Screenshot

![Permission Verified](../screenshots/permissions/05-read-permission-verified.png)

---

## Access-Control Process

```text
Parent Site Permissions
        │
        ▼
Inherited List Permissions
        │
        ▼
Stop Permission Inheritance
        │
        ▼
Unique List Permissions
        │
        ├── Owners → Full Control
        ├── Members → Edit
        └── Unnecessary Visitor Access Removed
                    │
                    ▼
             Test User Added
                    │
                    ▼
                  Read
                    │
                    ▼
          Permission Verified
```

---

## Security Principles Demonstrated

### Least Privilege

Users should receive only the permissions required to perform their responsibilities.

A user requiring visibility into the support list was therefore assigned **Read** rather than Edit or Full Control.

### Permission Inheritance

SharePoint resources can inherit permissions from their parent site. Breaking inheritance allows a list or library to maintain its own access configuration.

### Role-Based Access

Different permission levels were demonstrated for owners, members, and individual users.

### Permission Verification

Access configuration was verified rather than assuming the permission assignment was successful.

---

## Skills Demonstrated

* SharePoint Online Administration
* SharePoint Permissions
* Permission Inheritance
* Unique Permissions
* Access Control
* Least-Privilege Access
* User Permission Assignment
* Permission Verification
* Microsoft 365 Administration
* Identity and Access Management
* Security Troubleshooting
* Technical Documentation
