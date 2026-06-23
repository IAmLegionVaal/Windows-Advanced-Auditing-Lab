# Windows Advanced Auditing Lab

![Status](https://img.shields.io/badge/Project-Completed-success)
![Windows](https://img.shields.io/badge/Platform-Windows-0078D4)
![Auditing](https://img.shields.io/badge/Focus-Advanced%20Audit%20Policy-2F6FED)

A completed Windows security lab in which I configured advanced audit policies, generated controlled activity and validated the resulting security events for logon, account and object-access monitoring.

> **Status:** Completed and validated. This repository documents work already performed in a private lab. Real users, computer names, file paths, addresses and event records have been generalized.

## Objectives completed

- Reviewed basic and advanced audit-policy configuration
- Enabled selected success and failure subcategories
- Configured logon and account-logon auditing
- Enabled account-management auditing
- Configured object-access auditing for a test folder
- Generated controlled successful and failed activity
- Reviewed Security log event IDs and event details
- Validated policy application and documented findings

## Implementation summary

1. Reviewed the existing audit policy on the Windows endpoint.
2. Enabled selected advanced audit-policy subcategories.
3. Configured policy through local or domain Group Policy as appropriate.
4. Applied a SACL to a controlled test folder for object-access auditing.
5. Generated successful and failed sign-in attempts.
6. Created or modified controlled account and file activity.
7. Reviewed the resulting Security log events.
8. Correlated event time, account, source and object information.
9. Adjusted noisy or missing audit settings identified during testing.

## Validation commands

```cmd
auditpol /get /category:*
auditpol /get /subcategory:*
```

```powershell
Get-WinEvent -FilterHashtable @{ LogName = 'Security'; Id = 4624,4625,4720,4726,4663 } -MaxEvents 50
Get-Acl "C:\AuditTest" -Audit

gpresult /r
```

## Outcome

The configured policies produced Security log events for the selected successful and failed activities. The lab demonstrated how policy configuration, object-level SACLs and controlled test actions combined to create useful audit evidence.

## Findings

- Enabling object-access policy alone did not generate file events; the target object also required an appropriate SACL.
- Success and failure auditing answered different questions and had to be selected according to the monitoring goal.
- Broad auditing produced large volumes of low-value events, while targeted subcategories and objects created more useful evidence.
- Event IDs identified the activity type, but the event fields were necessary to understand the account, source, logon type and affected object.
- Time synchronization and consistent event retention were important for reliable investigation.
- Generating known test activity made it possible to prove that each audit control worked rather than assuming configuration alone was sufficient.

## Skills demonstrated

- Windows advanced audit policy
- Security event-log analysis
- Logon and account auditing
- Object-access auditing
- SACL configuration
- Event ID interpretation
- Group Policy validation
- Technical documentation

## Security notes

- No real credentials, personal records or production event data are included.
- All users, objects and paths are generalized.
- The lab was completed in a controlled non-production environment.

## Author

**Dewald Pretorius** — L2 IT Support Engineer
