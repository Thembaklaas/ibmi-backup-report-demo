# IBM i Backup Report Demo

A sanitized demonstration of an IBM i backup-status reporting workflow using Control Language (CL), embedded SQL, a spool/print file, PDF conversion, and email delivery.

> **Demo template, not a production-ready deployment.** The source was anonymized from a supplied example. Validate every command, SQL object, authority, and output format on a non-production IBM i partition before use.

## Repository layout

- `src/DEMOUPD2.clle` — collects backup, media, and IPL information; validates the result; coordinates formatting and report delivery.
- `src/DEMOFMT2.clle` — builds formatted report lines and copies them to the demo print file.
- `examples/demo-backup-report.pdf` — synthetic report output with illustrative values only.
- `docs/CONFIGURATION.md` — environment-specific setup notes.
- `SECURITY.md` — publication and secret-handling notes.

## Workflow

1. Clear and create temporary work tables.
2. Query the most recent backup record for a configured control group.
3. Validate that a backup record exists.
4. Retrieve associated media information.
5. Retrieve the latest IPL-related history entry within the configured window.
6. Format report lines.
7. Copy the formatted lines to a print file and initiate PDF/email delivery.
8. Send an escape message when a monitored failure occurs.

## Important configuration

The source uses generic names such as `DEMOLIB`, `DEMOUSR`, `DEMOCTL`, `DEMOPRTF2`, and `BRMSLIB`. These are placeholders, not guaranteed existing IBM i objects. See [Configuration](docs/CONFIGURATION.md) before attempting compilation or execution.

The recipient is set to `DEMO.USER@EXAMPLE.COM` as a placeholder. Do not use a real address in a public example repository.

## Suggested repository setup

Create a new public or private GitHub repository named `ibmi-backup-report-demo`, then upload the contents of this folder. Review the source and commit history before making it public; deleting a secret from the latest version does not remove it from earlier Git history.

## Limitations carried forward from the example

- A completed backup status indicates that BRMS recorded an end time; it does not prove every object was saved successfully.
- The sample logic captures only the first volume value from the backup row.
- BRMS catalog table/view names and fields can vary by IBM i / BRMS version and local configuration.
- Email delivery and spool-to-PDF behavior must be verified in the target environment.
- This repository has not been compiled or executed against an IBM i system.
