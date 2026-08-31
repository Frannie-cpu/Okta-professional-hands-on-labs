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
   
- Created a new user/employee **(Cisca Joseph)** manually through **Directory** → **People**
  
[Added Cisca Joseph as new employee](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/Provisioning%20Add%20user.png)

- I used Admin-set password for Cisca Joseph and observed initial **Staged** status prior to activation.

[Cisca Joseph's account was created but not activated, resulting in staged status](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/staged%20unactivated%20user.png)

[System awaiting user activation](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/pending%20user%20action%20to%20activate%20account.png)

- Cisca Joseph receives okta activation email and they are required to set their desired password.

[Cisca Joseph receives okta account activation email](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/New%20user%20activation%20email.PNG)

[Cisca Joseph receives okta verify activation email for mfa](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/New%20user%20okta%20verify%20setup.PNG)

[Cisca Joseph is required to create a new password for their okta account](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/New%20user%20password%20set%20up.PNG)

- Once Cisca Joseph activates their okta account and changes to a desired password, status on OKTA changes from **Staged** to **Active**
  
[Activated user and confirmed transition to Active,thereby enabling authentication](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/User%20activation%20changed%20status%20to%20Active.png)


- I tested Cisca Joseph's ability to log in. See 4 screenshots below.

[Cisca Joseph enters username](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/Testing%20provisioned%20user%201.png)

[Cisca Joseph their password](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/Testing%20provisioned%20user%20II.png)

[Cisca Joseph is prompted to enter code for okta verify authenticator app](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/Testing%20provisioned%20user%20III.png/)

[Cisca Joseph successfully signed on OKTA using their credentials](https://github.com/Frannie-cpu/Okta-professional-hands-on-labs/blob/main/Lab-02-User-Lifecycle/screenshots/Testing%20provisioned%20user%20IIII.png)






