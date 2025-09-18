Introduction

This lab report analyzes logic bombs using the “Logic Bombs: Lessons from Real Cases” material as the case study. A logic bomb is malicious code intentionally hidden in software that triggers a harmful action when specific conditions are met (a date, the deletion of a user account, the presence/absence of a file, etc.). This report describes the malware type, likely infection methods and observable symptoms, suggested evidence to collect during a guided simulation, recommended defenses and mitigations (minimum three), and a connection to NetAcad Modules 2.1–2.2. The goal is to translate case lessons (UBS, Omega, Siemens) into practical lab observations and organizational controls.

Malware Type

Name / Type: Logic bomb (insider-laid timed or conditional sabotage)

Definition: A logic bomb is malicious payload code embedded within legitimate software or scripts that remains dormant until specific conditions occur. Unlike worms or viruses, logic bombs are typically planted by insiders with authorized access and rely on those privileges and often human action (or a triggering condition) rather than external propagation techniques.

Key characteristics:

Dormant until a triggering condition (date, system event, account termination).

Often embedded in maintenance scripts, scheduled tasks, macros, or configuration files.

Designed for data destruction, denial of service, or to force repeated dependence on a malicious maintainer.

Infection Method & Symptoms

Infection / Placement Methods (based on guided lab scenarios):

Embedded within administrative scripts or batch jobs that run periodically.

Hidden in macros inside spreadsheets or documents used by operations teams.

Inserted in configuration files or executables maintained by a single contractor or admin.

Left as scheduled tasks/cron jobs that execute under privileged accounts.

Symptoms observed or likely during simulation:

Sudden mass deletion or modification of files at the trigger time (e.g., midnight on a specific date).

Previously stable scripts or spreadsheets producing errors or malformed output.

New or unexpected scheduled tasks (Windows Task Scheduler or cron entries).

Unusual registry key modifications (on Windows) or new startup scripts (on Linux).

Spike in help-desk or application error tickets coinciding with the trigger.

Repeated calls to an external contractor or user who ‘maintains’ the broken scripts (as seen in cases).

Evidence (to collect during the guided lab)

Note: Replace the placeholder/example entries below with your actual lab logs, screenshots, and notes gathered during Monday’s lab.

1. System & Application Logs

Example Windows Event Viewer entry (sample):

5. Notes / Chronology

Timeline: account termination or grievance → logic bomb planting (date/time) → trigger event → incident detection and response times.

Defenses & Mitigations (minimum three)

Strict Separation of Duties & Code Ownership

Ensure no single person has unilateral control over production scripts, builds, and scheduled tasks. Require peer ownership and documented handoff for all operational scripts and macros.

Comprehensive Off-boarding & Credential Rotation

Immediately revoke user and service account credentials upon termination or role change; rotate service account keys; audit scheduled tasks and scripts as part of exit checklists.

Change Control, Code Review, and Versioning

Require peer review and commit history for all scripts/configuration that run on production systems. Store code in version control with access controls and automated CI checks to reject time-based destructive code.

Monitoring & Integrity Checking

Use EDR/IDS and file integrity monitoring to alert on new scheduled tasks, unusual file deletions, or modifications of critical scripts. Correlate alerts with HR events.

Backups + Rapid Recovery Playbooks

Maintain immutable, tested backups (air-gapped or offline snapshots) and rehearse recovery to reduce impact from destructive triggers.

Connection to NetAcad Modules 2.1–2.2

NetAcad Module 2.1 introduces the threat landscape and distinguishes malware categories; logic bombs are an insider-driven variant that reinforces the module’s emphasis on human factors in cybersecurity. Module 2.2 covers defensive fundamentals—least privilege, access control, and incident response—which align directly with the mitigations above (separation of duties, off-boarding, monitoring, and backups). The lab connects theory to practice by showing how weak operational controls allow logic bombs to persist and how the modules’ recommended controls reduce that risk.

Conclusion

Logic bombs demonstrate how trusted access can be weaponized to cause significant operational and financial damage. The three real-world cases underline a common pattern: privileged insiders place dormant destructive code in operational artifacts and rely on infrequent checks or human workflows to escape detection. Preventing logic bombs requires organizational discipline—separation of duties, enforced change control, immediate off-boarding, continuous monitoring, and reliable backups. In the guided lab, evidence collection focused on logs, scheduled task listings, script reviews, and file-system snapshots—these artifacts form the basis of detection and post-incident recovery.
