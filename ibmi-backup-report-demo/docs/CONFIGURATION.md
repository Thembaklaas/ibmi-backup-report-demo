# Configuration notes

This is a sanitized template. Object names below are examples and must be mapped to objects that exist in an isolated IBM i test environment.

## Names to review

| Placeholder | Purpose |
|---|---|
| `DEMOLIB` | Demo library for work tables and the print file |
| `DEMOUSR` | Demo source library/user namespace for source members and programs |
| `DEMOCTL` | Example backup control group |
| `BRMSLIB` | Placeholder for the BRMS catalog library/schema containing the referenced backup and media objects |
| `DEMOPRTF2` | Demo print file |
| `DEMO.USER@EXAMPLE.COM` | Non-deliverable example email address |

IBM-provided system interfaces such as `QSYS2.HISTORY_LOG_INFO`, the `QSYSOPR` message queue, and `QCPFMSG` are retained where used because they are standard IBM i interfaces, not organization-specific identifiers. Confirm they are appropriate for your platform and authority model.

## Setup checklist

1. Use a non-production IBM i partition or a dedicated test environment.
2. Create a demo library and a print file with a record format compatible with the report output.
3. Confirm the exact BRMS catalog object names and columns for your installed release. Update `BRMSLIB` and any field references accordingly.
4. Create source members from the `.clle` files, adjusting source-file and program names to your site's naming standards.
5. Compile the formatter before the driver.
6. Confirm the spool file can be converted to PDF and that outbound email is disabled or directed to a controlled test mailbox.
7. Test missing backup rows, active backups, stale backups, missing media rows, SQL failures, and email/PDF failures.
8. Review job logs and authorities before enabling any scheduled execution.

## Safety note

Do not copy commands into a live system without a peer review. Placeholder substitutions alone do not make the code safe for production.
