# Lab 02 – User Lifecycle Management

## Objective
To implement and analyze User Lifecycle Management (ULM) in Okta by creating users, managing lifecycle state transitions (Staged, Active, Suspended, Locked Out, Deactivated), and evaluating how each state impacts authentication and application access.

##Architecture Diagram
(insert lucidchart diagram with description footer text This architecture demonstrates how user lifecycle states in Okta affect authentication and downstream application access. Administrative actions directly influence user status and access permissions.)

## Configuration Steps
1. User Creation (Joiner Phase)
Created user in Directory → People
Tested both:
Admin-set password
User-activated via email
Observed initial Staged status prior to activation
(Insert screenshot here titled User account was created but not activated, resulting in staged status)
Activated user and confirmed transition to Active
(Insert screenshot here titled Activation changed status to Active, enabling authentication)


3. Suspension (Temporary Access Restriction)

Suspended active user account
Attempted login via incognito session
(Insert screenshot here titled Suspended users cannot log in but retain assignments)

5. Deactivation (Leaver Phase)
Deactivated user account
Verified: Access revoked, Sessions terminated, Application access removed
IAM insight: Deactivation enforces complete access revocation and is used during employee offboarding

6. Password Reset
Initiated admin password reset
Verified session invalidation behavior
Security Insight: Password resets invalidate active sessions, reducing account compromise risk
(Insert screenshot here titled Deactivation revoked access and terminated active sessions)

5.Account Lockout Simulation
Triggered lockout via failed login attempts
Reviewed lockout event in System Log
Unlocked user via admin action
IAM Insight:Lockout protects against brute-force attacks while preserving access assignments
(Insert screenshot here titled System Log shows failed authentication attempts leading to lockout)

## Expected Behavior/Result
- User receives activation email
- Access granted based on group membership
- User successfully provisioned and able to authenticate
- Suspended user authentication blocked while group and application assignments remained intact
IAM Insight:Suspension is used for temporary access restriction without removing entitlements

## Troubleshooting Scenario
Issue: Unsuccessful log in
User reports authentication failure
Investigation Steps:
1. Navigated to Reports → System Log
2. Filtered logs by username
3. Identified event type: user.session.start
4. Observed failure reason: Account locked due to multiple failed attempts.
Root Cause:
 Exceeded password policy lockout threshold.
How i resolved the issue:
   Unlocked user account
Prevention:
 Reviewed password policy and user awareness.

## Screenshots
(Insert all screenshots mentioned above)

## What is User Lifecycle Management?
User Lifecycle Management (ULM) is the process of managing digital identities from account creation to deactivation, ensuring proper access control throughout the user’s relationship with the organization
Proper lifecycle management:Prevents orphaned accounts, reduces insider risk, enforces least privilege and ensures timely access revocation
Lifecycle Phases in IAM are-
Joiner- Account creation and access provisioning
Mover- Role change and access modification
Leaver- Access revocation and account deactivation




