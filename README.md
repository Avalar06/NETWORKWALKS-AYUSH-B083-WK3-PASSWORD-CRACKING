# NetworkWalks Week 3 — Password Cracking

This repository contains the practical work completed for the NetworkWalks cybersecurity internship, Week 3.

## Modules

- **PM1 — Password Cracking with JTR**
- **PM2 — Password Cracking with NetworkWalks Tools**

The work was performed as an authorized cybersecurity training exercise using internship-provided password-protected PDF files.

## Objective

Understand the password-recovery workflow for protected PDFs: extract a crackable PDF hash, supply the hash to a password-auditing tool, perform the permitted dictionary-based recovery exercise, and verify the recovered password against the protected file.

## Environment

- Operating system: Windows
- John the Ripper: **1.9.0-jumbo-1 64-bit Windows build**
- Johnny: **2.2**
- Browser-based NetworkWalks Hash Calculator and Password Cracker for PM2
- Internship-provided protected PDF training files

## PM1 — JTR / Johnny

### Workflow

```text
Protected PDF
  -> PDF hash extraction
  -> $pdf$... hash
  -> hash1.txt
  -> Johnny GUI
  -> John the Ripper
  -> recovered password
  -> PDF verification
  -> NetworkWalks flag
```

### Findings

- Located the JTR `john.exe` executable in the JTR `run` directory.
- Installed Johnny and configured it to use `john.exe`.
- Johnny detected **John the Ripper 1.9.0-jumbo-1 OMP [Cygwin 64-bit x86_64 AVX2 AC]**.
- Extracted a crackable `$pdf$...` hash from the protected PDF.
- Saved the complete hash as `hash1.txt`.
- Loaded the hash into Johnny; the entry was recognized as **PDF**.
- The attack reached **100%** and Johnny reported **1/1 cracked, 0 left**.
- The observed recovered training password was **password1**.
- The protected PDF was successfully opened using the recovered password.
- A NetworkWalks congratulations/flag screen was captured.

## PM2 — NetworkWalks Tools

### Workflow

```text
Protected PDF
  -> NetworkWalks Hash Calculator
  -> $pdf$... hash
  -> NetworkWalks Password Cracker
  -> built-in dictionary
  -> recovered password
  -> PDF verification
  -> NetworkWalks flag
```

### Findings

- Selected **PDF** mode in the NetworkWalks Hash Calculator.
- Processed `My-Locked-PDF1.pdf`.
- The tool identified the file as encrypted and produced a crackable `$pdf$...` hash.
- Reported parameters visible in the tool: **Revision R4, Version V4, Key length 128 bit**.
- Supplied the complete hash to the NetworkWalks Password Cracker.
- Used the built-in **100-password** list.
- The tool reported **PASSWORD CRACKED SUCCESSFULLY** with the match **password1**.
- The visible success point showed **91/100 tried** at approximately **9 p/s**.
- The recovered password successfully opened the protected PDF.

## Additional Protected PDFs

During the practical session, the supplied **My-Locked-PDF2.pdf** and **My-Locked-PDF3.pdf** were also opened successfully using the recovered training password. Each displayed a NetworkWalks congratulations/flag screen.

These are documented as additional observed training artifacts. The supplied PM1 and PM2 task sheets explicitly name **My Locked PDF1.pdf** as the task file, so the report distinguishes the official named task from these additional observations.

## Evidence

Evidence should demonstrate:

- JTR package and `john.exe`
- Johnny installation/configuration
- PDF hash extraction
- `hash1.txt`
- Hash loaded into Johnny
- JTR completion and recovered result
- NetworkWalks Hash Calculator result
- NetworkWalks Password Cracker result
- PDF verification and flag screens
- Additional PDF2/PDF3 verification screens

## Security and Ethics

This is an authorized training lab. Password-recovery tools must only be used against files, systems, or accounts for which testing is explicitly permitted.

Do not publish API tokens, unrelated private information, or unnecessary reusable credentials in a public repository. Keep original protected PDFs and other sensitive training artifacts outside the public repository unless the internship explicitly requires public submission.

## Learning Outcomes

- Understood protected-file password recovery at a practical level.
- Learned PDF hash extraction and `$pdf$` hash handling.
- Configured Johnny to use John the Ripper.
- Performed a dictionary-based recovery exercise.
- Verified recovered credentials against protected PDFs.
- Collected reproducible cybersecurity evidence.
- Understood the defensive value of strong and unique passwords.

## Status

**Week 3 practical work completed.**

The final report and evidence package are being organized for internship submission.
