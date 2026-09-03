# Lab 02 – User Lifecycle Management

## What is User Lifecycle Management?
User Lifecycle Management (ULM) is the process of managing digital identities from account creation to deactivation, ensuring proper access control throughout the user’s relationship with the organization.
Proper lifecycle management prevents orphaned accounts, reduces insider risk, enforces least privilege and ensures timely access revocation.


## Overview

User Lifecycle Management (ULM) is the process of managing digital identities throughout a user's relationship with an organization — from onboarding and access provisioning to role changes and eventual offboarding.

This architecture demonstrates how **Okta** can act as the central Identity Provider (IdP) for managing identity lifecycle events, access control, authentication, authorization, and Single Sign-On (SSO) while applying identity governance and security controls across the environment.

The architecture follows the three major lifecycle stages:

* **Joiner** — Create the user's identity and provision appropriate access
* **Mover** — Modify the user's role, groups, and application access when responsibilities change
* **Leaver** — Revoke access and deactivate the identity when the user leaves the organization

---

## Architecture

```text
                     HR / IDENTITY SOURCE
                              │
                              │ Employee + Role
                              ▼
                         ┌─────────┐
                         │  OKTA   │
                         │   IdP   │
                         └────┬────┘
                              │
             ┌────────────────┼────────────────┐
             ▼                ▼                ▼
          JOINER            MOVER            LEAVER
             │                │                │
             ▼                ▼                ▼
     Create identity    Modify access     Revoke access
     + provision        / groups          / deactivate
        access
             │                │                │
             └────────────────┼────────────────┘
                              ▼
                     ┌──────────────────┐
                     │  ACCESS CONTROL  │
                     │                  │
                     │ Groups           │
                     │ Roles            │
                     │ App Assignments  │
                     │ Policies         │
                     └────────┬─────────┘
                              │
                 ┌────────────┴────────────┐
                 ▼                         ▼
        ┌─────────────────┐       ┌─────────────────┐
        │ AUTHENTICATION  │       │  AUTHORIZATION  │
        │                 │       │                 │
        │ • Credentials   │       │ • Groups        │
        │ • MFA           │       │ • Roles         │
        │ • Auth Policies │       │ • App Assignment│
        │                 │       │ • Entitlements  │
        │ "Who are you?"  │       │ "What can you    │
        │                 │       │  access?"       │
        └────────┬────────┘       └────────┬────────┘
                 │                         │
                 └────────────┬────────────┘
                              ▼
                     ┌──────────────────┐
                     │  ACCESS DECISION │
                     │                  │
                     │  ALLOWED /       │
                     │  DENIED          │
                     └────────┬─────────┘
                              │
                              ▼
                         ┌─────────┐
                         │ OKTA SSO│
                         └────┬────┘
                              │
                 ┌────────────┼────────────┐
                 ▼            ▼            ▼
              SaaS Apps      CRM          ITSM


╔════════════════════════════════════════════════════════════════════╗
║             IDENTITY GOVERNANCE & SECURITY CONTROLS               ║
║                                                                    ║
║ Least Privilege │ Access Reviews │ Access Requests                ║
║ Entitlement Management │ Audit & Logging │ Monitoring             ║
║ Policy Enforcement │ Compliance │ Separation of Duties             ║
╚════════════════════════════════════════════════════════════════════╝
```

---
IAM extends beyond simply creating user accounts. It is a continuous process of **establishing identity, managing access, verifying users, enforcing authorization, monitoring activity, and governing access throughout the identity lifecycle.**

## Identity Governance & Security Controls

* **Least Privilege** — Users receive only the access required for their job.
* **Access Reviews** — User access is periodically reviewed and approved or revoked.
* **Access Requests** — Additional access is requested and approved through a controlled process.
* **Entitlement Management** — Specific permissions within applications are managed and governed.
* **Separation of Duties (SoD)** — Conflicting responsibilities are separated to reduce risk.
* **Audit & Logging** — Identity and access activities are recorded for investigation and accountability.
* **Monitoring** — Identity activity is monitored for unusual or potentially risky behavior.
* **Policy Enforcement** — Security and access policies are consistently applied to user access.
* **Compliance** — Access controls and records support regulatory and organizational requirements.


## Security Objective

The architecture is designed around the principle of:

> **Right user → Right access → Right time → Right level of privilege**

The lifecycle model helps ensure that:

* New employees receive appropriate access
* Existing employees receive access appropriate to their current roles
* Unnecessary access is removed when responsibilities change
* Departing employees have access revoked
* Authentication requirements are enforced
* Authorization determines permitted application access
* Application access can be centrally managed
* Access can be reviewed and governed over time
* Identity activity can be monitored and audited

---
---


The initial goal was to analyse User Lifecycle Management (ULM) in Okta by creating users, managing lifecycle state transitions (Staged, Active, Suspended, Locked Out, Deactivated), and evaluating how each state impacts authentication and application access. 

**However, I was able to only cover the User Creation (Joiner Phase) with Authentication on OKTA. 
See a [more extensive IAM project](https://github.com/Frannie-cpu/iam-project) on Microsoft Entra ID**


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






