# Lab 02 – User Lifecycle Management

## Objective
To implement and analyze User Lifecycle Management (ULM) in Okta by creating users, managing lifecycle state transitions (Staged, Active, Suspended, Locked Out, Deactivated), and evaluating how each state impacts authentication and application access.

##Architecture Diagram
(insert lucidchart diagram with description footer text This architecture demonstrates how user lifecycle states in Okta affect authentication and downstream application access. Administrative actions directly influence user status and access permissions.)

## Configuration Steps
### 1. User Creation (Joiner Phase)

Created 2 users manually through **Directory → People**.

Tested both: 
- User-activated via email for first user
- Admin-set password for second user 

Observed initial **Staged** status prior to activation for first user  
(Insert screenshot here titled *"User account was created but not activated, resulting in staged status"*).

User receives activation email and sets their desired password.
Activated user and confirmed transition to **Active**.  
(Insert screenshot here titled *"Activation changed status to Active, enabling authentication"*).

Tested new users ability to log in. see 4 screenshots.


## What is User Lifecycle Management?
User Lifecycle Management (ULM) is the process of managing digital identities from account creation to deactivation, ensuring proper access control throughout the user’s relationship with the organization
Proper lifecycle management:Prevents orphaned accounts, reduces insider risk, enforces least privilege and ensures timely access revocation
Lifecycle Phases in IAM are-
Joiner- Account creation and access provisioning
Mover- Role change and access modification
Leaver- Access revocation and account deactivation




