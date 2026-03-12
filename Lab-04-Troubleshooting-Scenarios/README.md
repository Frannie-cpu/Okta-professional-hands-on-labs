Password reset
Account lockout

## Troubleshooting Scenario
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
   Unlocked user account
Prevention:
 Reviewed password policy and user awareness.

 ### 5. Account Lockout Simulation

Triggered lockout via failed login attempts.

Reviewed lockout event in **System Log**.

Unlocked user via admin action.

**IAM Insight:**  
Lockout protects against brute-force attacks while preserving access assignments.

(Insert screenshot here titled *"System Log shows failed authentication attempts leading to lockout"*).
