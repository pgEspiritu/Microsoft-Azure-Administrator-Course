# 🔐 Module 1: Administer Identity

# 📚 Lessons Overview

This module focuses on managing identities in Microsoft Entra ID. It covers the fundamentals of identity management, user and group administration, property management, and external collaboration.

---

# 🧠 Lesson 1: Understand Microsoft Entra ID

## 📖 What is Microsoft Entra ID?

Microsoft Entra ID is a cloud-based **Identity and Access Management (IAM)** service that helps organizations securely manage:
- 👤 Users
- 👥 Groups
- 💻 Devices
- 📦 Applications
- 🔐 Access permissions

It allows users to securely sign in and access organizational resources.

---

# ⭐ Key Concepts of Microsoft Entra ID

## 🔑 Authentication
Verifies the identity of users during sign-in.

### Examples
- Password login
- Multi-Factor Authentication (MFA)
- Biometrics
- Passwordless sign-in

---

## 🛡️ Authorization
Determines what users are allowed to access after authentication.

### Examples
- Access to Microsoft 365
- Access to applications
- Access to Azure resources

---

## ☁️ Cloud Identity
Microsoft Entra ID stores user identities in the cloud for centralized access management.

### Benefits
- 🌍 Access anywhere
- ☁️ Cloud scalability
- 🏢 Hybrid environment support
- ⚡ Simplified administration

---

## 🔗 Single Sign-On (SSO)

SSO allows users to sign in once and access multiple applications.

### Example
A user signs in once and gains access to:
- Outlook
- Teams
- SharePoint
- OneDrive

---

## 📱 Multi-Factor Authentication (MFA)

Adds additional security verification beyond passwords.

### MFA Methods
- Authenticator app
- SMS code
- Phone call
- Security keys

---

## 🚦 Conditional Access

Applies security policies based on:
- User location
- Device compliance
- Risk level
- Application sensitivity

---

# 👥 Lesson 2: Create Users and Groups

# 👤 Creating Users in Microsoft Entra ID

Administrators create user accounts for employees, students, or other users.

---

## 📌 User Information

When creating a user, administrators configure:
- Display name
- Username (UPN)
- Password
- Job title
- Department
- Location

---

## 🛠️ Steps to Create a User

### Using Microsoft Entra Admin Center

1. Open Microsoft Entra Admin Center
2. Navigate to:
   - 👥 Identity → Users
3. Click ➕ **New User**
4. Select:
   - Create new user
5. Enter user information
6. Assign password
7. Click ✅ Create

---

# 👥 Creating Groups

Groups organize users for easier access and permission management.

---

## 📦 Types of Groups

| Group Type | Purpose |
|---|---|
| Security Group | Manage permissions |
| Microsoft 365 Group | Collaboration and communication |
| Dynamic Group | Automatic membership assignment |

---

## 🔐 Security Groups

Used for:
- Application access
- Security permissions
- Policy assignment

---

## 📧 Microsoft 365 Groups

Provide:
- Shared mailbox
- Teams integration
- SharePoint access
- Collaboration tools

---

## ⚡ Dynamic Groups

Automatically add users based on rules.

### Example Rule
> Add all users from the HR department automatically.

---

# 🛠️ Steps to Create a Group

1. Open Microsoft Entra Admin Center
2. Go to:
   - 👥 Groups
3. Click ➕ **New Group**
4. Choose group type
5. Enter:
   - Group name
   - Description
6. Add members
7. Click ✅ Create

---

# ⚙️ Lesson 3: Manage Users and Group Properties

# 👤 Managing User Properties

Administrators can update and maintain user account information.

---

## 📌 Common User Properties

| Property | Description |
|---|---|
| Display Name | User’s full name |
| Username | Login account |
| Email Address | Contact email |
| Department | Organizational unit |
| Job Title | Position |
| Office Location | User location |
| Phone Number | Contact number |

---

# 🔄 Common User Management Tasks

## ✏️ Edit User Information
Update user details when:
- Employee changes department
- User changes contact information
- Job title changes

---

## 🔑 Reset Passwords

Administrators can:
- Reset passwords manually
- Enable Self-Service Password Reset (SSPR)

---

## 🚫 Disable User Accounts

Used when:
- Employee leaves organization
- Account is temporarily suspended

---

## ❌ Delete User Accounts

Removes users permanently from Microsoft Entra ID.

---

# 👥 Managing Group Properties

Administrators manage:
- Group names
- Descriptions
- Membership
- Group owners

---

## ➕ Add or Remove Members

Users can be:
- Added manually
- Removed manually
- Managed dynamically

---

## 👑 Assign Group Owners

Group owners can:
- Manage memberships
- Update group settings
- Maintain collaboration resources

---

# 🔐 Group-Based Access Management

Groups simplify permission assignment.

### Example
Instead of assigning permissions individually:
- Assign permissions to a group
- Add users to the group

---

# 🌐 Lesson 4: Manage External Users

# 👤 What are External Users?

External users are users outside the organization who need temporary or limited access.

### Examples
- Vendors
- Consultants
- Business partners
- Contractors

---

# 🌍 Azure AD B2B Collaboration

Microsoft Entra ID uses **Business-to-Business (B2B)** collaboration for external access management.

---

# 📧 Inviting External Users

Administrators invite guest users using email addresses.

---

## 🛠️ Steps to Invite Guest Users

1. Open Microsoft Entra Admin Center
2. Navigate to:
   - 👥 Users
3. Click ➕ **New Guest User**
4. Enter guest email address
5. Add optional message
6. Click 📧 Invite

---

# 📨 Guest User Invitation Process

1. Guest receives invitation email
2. Guest accepts invitation
3. Guest account is created in Microsoft Entra ID
4. Guest receives limited access

---

# 🔐 Managing Guest User Permissions

Guest users usually receive:
- Limited access
- Specific application permissions
- Restricted organizational visibility

---

# 🚦 Security for External Users

Organizations can apply:
- MFA requirements
- Conditional Access policies
- Access reviews
- Expiration policies

---

# 🔍 Monitoring External Users

Administrators can monitor:
- Sign-in activities
- Access history
- Security risks
- Audit logs

---

# 🛡️ Best Practices for Managing External Users

## ✅ Use Least Privilege Access
Grant only the permissions needed.

---

## ✅ Enable MFA
Protect guest accounts with Multi-Factor Authentication.

---

## ✅ Regularly Review Access
Remove unused guest accounts.

---

## ✅ Apply Conditional Access
Restrict access based on:
- Device
- Location
- Risk level

---

# 🎯 Summary of Module 1

| Lesson | Main Topic |
|---|---|
| Understand Microsoft Entra ID | Identity and access management concepts |
| Create Users and Groups | Creating and organizing identities |
| Manage Users and Group Properties | Maintaining user and group information |
| Manage External Users | Secure collaboration with external users |

---

# 📝 Overall Summary

Module 1 focuses on administering identities in Microsoft Entra ID. It teaches administrators how to understand identity concepts, create and manage users and groups, maintain user and group properties, and securely collaborate with external users using Microsoft Entra ID features and security controls.
