# Changelog

## Week 3 — Password Cracking

### Repository Setup
- Created the dedicated public Week 3 repository.
- Added the repository-level README with the complete Week 3 scope, methodology, findings, evidence index, security considerations, and final status.
- Added separate documentation for PM1 and PM2.
- Created dedicated evidence directories for PM1 and PM2.

### PM1 — JTR / Johnny
- Prepared the John the Ripper 1.9.0-jumbo-1 64-bit Windows package.
- Located the JTR `run\\john.exe` executable.
- Installed Johnny 2.2.
- Configured Johnny to use the JTR executable.
- Verified JTR engine detection as **1.9.0-jumbo-1 OMP [Cygwin 64-bit x86_64 AVX2 AC]**.
- Extracted the protected PDF's `$pdf$...` hash.
- Saved the extracted hash locally as `hash1.txt`.
- Loaded the hash into Johnny and verified **PDF** format recognition.
- Completed the cracking run with **1/1 cracked, 0 left**.
- Recovered the supplied training password.
- Verified the password by opening the protected PDF.
- Captured the NetworkWalks verification/flag screen.
- Uploaded and organized the verified PM1 PNG evidence.

### PM2 — NetworkWalks Tools
- Opened the NetworkWalks Hash Calculator.
- Selected PDF mode and processed the named training PDF.
- Confirmed encrypted-PDF detection and crackable `$pdf$...` hash extraction.
- Recorded the visible PDF parameters: **Revision R4, Version V4, Key length 128 bit**.
- Supplied the complete extracted hash to the NetworkWalks Password Cracker.
- Used the built-in **100-password** candidate list.
- Completed the dictionary-based recovery exercise and recorded the successful match.
- Recorded the visible success point of approximately **91/100 tried** and **9 p/s**.
- Verified the recovered password by opening the protected PDF.
- Captured the NetworkWalks verification/flag evidence.
- Verified the supplied PDF2 and PDF3 training artifacts as supplementary results.
- Uploaded and organized the verified PM2 PNG evidence.

### Evidence and Documentation
- Replaced generic evidence-folder instructions with summaries of the actual uploaded PNG files.
- Added descriptive evidence naming and chronological evidence mapping.
- Kept original protected PDFs and complete reusable hashes out of the public repository.
- Updated the repository documentation to distinguish the primary named task file from supplementary PDF2/PDF3 observations.
- Finalized the repository README and evidence organization for the Week 3 internship submission.

## Current Status

**Week 3 practical execution: completed.**

**Repository evidence and documentation: organized.**

**Final internship report: pending final assembly from the verified evidence set.**
