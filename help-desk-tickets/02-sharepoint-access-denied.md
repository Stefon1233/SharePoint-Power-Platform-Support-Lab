# Ticket 02 — SharePoint Access Denied

## Ticket Information

- **Requester:** John Smith
- **Department:** IT
- **Category:** Account Access
- **Priority:** Medium
- **Assigned Technician:** Stefon Kreller
- **Status:** Resolved

## Issue

The user reported being unable to access the SharePoint IT support resources 
required for their technician responsibilities.

## Investigation

1. Reviewed the user's SharePoint access.
2. Reviewed the permissions assigned to the IT support resources.
3. Verified Microsoft Entra ID group membership.
4. Confirmed the technician security group was configured with SharePoint Edit 
permission.
5. Used SharePoint's Check Permissions feature to verify the user's effective 
access.

## Resolution

The user was added to the Microsoft Entra ID security group:

`SG-IT-Support-Technicians-Security`

The security group was configured with **Edit** access to the SharePoint support 
environment.

SharePoint's Check Permissions feature confirmed that John Smith received 
**Edit** access through the security group.

## Access Model

User access was provided through group membership rather than through an 
individual Edit permission assignment:

John Smith  
→ SG-IT-Support-Technicians-Security  
→ SharePoint Edit Permission  
→ IT Support Resources

## Result

The technician's required SharePoint access was verified successfully.

Using a Microsoft Entra ID security group provides a more scalable method of 
managing technician access because users can be added to or removed from the 
group as their responsibilities change.

## Technologies Used

- Microsoft Entra ID
- SharePoint Online
- Security Groups
- SharePoint Permissions
- Microsoft 365
- Identity and Access Management
