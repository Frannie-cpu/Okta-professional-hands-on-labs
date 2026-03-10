### Group-Based Access Control (RBAC)

This section demonstrates how **role-based access control (RBAC)** was implemented using groups.  
Instead of assigning permissions to individual users, access is managed through **groups**, allowing scalable and consistent identity management.

---

#### 1. Creating a Role-Based Group

Added "Title and Description" attributes to newly created user profile.
Title: Techinical Support Specialist and Description: Engineering
Created a new group in **Directory → Groups** to represent a role within the organization.

Example configuration:
- **Group Name:** Engineering
- **Description:** Provides access to engineering-related applications and resources.

Purpose:
- Centralize permission management
- Reduce manual user-level access assignments
- Align access with organizational roles

(Insert screenshot here titled *"Engineering-Team group created for role-based access control"*)

---

#### 2. Configuring Group Rules (Automated Membership)

Configured a **Group Rule** to automatically assign users to the group based on user profile attributes.

Example rule condition:
- If `Department = Engineering`
- Then assign user to **Engineering-Team** group.

Verification:
- Newly created users with the Engineering department attribute were automatically added to the group.

IAM Insight:  
Group rules automate identity governance by ensuring users receive access based on **organizational attributes rather than manual assignments**.

(Insert screenshot here titled *"Group rule automatically assigns Engineering users to Engineering-Team group"*)

---

#### 3. Automating Application Provisioning

Assigned applications to the **Engineering-Team** group to automate access provisioning.

Provisioning workflow verified:
1. User account created
2. Group rule assigns user to Engineering-Team
3. Application access automatically provisioned through group membership

Benefits:
- Consistent access control
- Reduced administrative overhead
- Faster onboarding for new users

IAM Insight:  
Group-based provisioning supports **scalable identity lifecycle management** by linking user roles directly to application access.

(Insert screenshot here titled *"Application access automatically provisioned through group membership"*)
