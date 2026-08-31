# Lab 02 – User Lifecycle Management

## What is User Lifecycle Management?
User Lifecycle Management (ULM) is the process of managing digital identities from account creation to deactivation, ensuring proper access control throughout the user’s relationship with the organization
Proper lifecycle management:Prevents orphaned accounts, reduces insider risk, enforces least privilege and ensures timely access revocation

Lifecycle Phases in IAM are-

**Joiner**- Account creation and access provisioning

**Mover**- Role change and access modification

**Leaver**- Access revocation and account deactivation


## Objective
To implement and analyze User Lifecycle Management (ULM) in Okta by creating users, managing lifecycle state transitions (Staged, Active, Suspended, Locked Out, Deactivated), and evaluating how each state impacts authentication and application access. 

However, this page could only covers one User Creation (Joiner Phase)

##Architecture Diagram
(insert lucidchart diagram with description footer text This architecture demonstrates how user lifecycle states in Okta affect authentication and downstream application access. Administrative actions directly influence user status and access permissions.)

## Configuration
**User Creation (Joiner Phase)**
   
- Created 2 users manually through **Directory** → **People**


- I used Admin-set password for one user and observed initial **Staged** status prior to activation.

[User account was created but not activated, resulting in staged status](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/staged%20unactivated%20user.png)

[System awaiting user activation](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/pending%20user%20action%20to%20activate%20account.png)

- User receives activation email and sets their desired password. 

[Activated user and confirmed transition to Active,thereby enabling authentication](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/User%20activation%20changed%20status%20to%20Active.png)


- Tested new user's ability to log in. See 4 screenshots below.

[User enters username](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/Testing%20provisioned%20user%201.png)

[User enters their password](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/Testing%20provisioned%20user%20II.png)

[User is prompted to enter code for okta verify authenticator app](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/Testing%20provisioned%20user%20III.png/)

[User enters username](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/Testing%20provisioned%20user%20IIII.png)






