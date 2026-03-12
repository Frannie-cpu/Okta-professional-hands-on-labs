
## Troubleshooting Scenario

### 1. Password Reset

Initiated admin password reset

Verified session invalidation behavior

**Security Insight:**  Password resets invalidate active sessions, reducing account compromise risk

 ### 2. Account Lockout Simulation
I triggered lockout via failed login attempts
Issue: Unsuccessful log in
User reports authentication failure
Investigation Steps:
- Navigated to Reports → System Log
- Filtered logs by username
- Identified event type: user.session.start
- Observed failure reason: Account locked due to multiple failed attempts.
Root Cause:
 Exceeded password policy lockout threshold.
How i resolved the issue:
   Unlocked user account via admin action
Prevention:
 Reviewed password policy and user awareness.

**IAM Insight:**  
Lockout protects against brute-force attacks while preserving access assignments.

(Insert screenshot here titled *"System Log shows failed authentication attempts leading to lockout"*).
