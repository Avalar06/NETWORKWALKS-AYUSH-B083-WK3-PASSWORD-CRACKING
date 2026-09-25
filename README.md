# NetworkWalks Week 3 — Password Cracking

![NetworkWalks](https://img.shields.io/badge/NetworkWalks-Week%203-blue)
![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-red)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Platform](https://img.shields.io/badge/Platform-Windows-0078D6)

This repository documents the practical cybersecurity work completed during **NetworkWalks Week 3**, focused on password auditing and password-recovery techniques against authorized, internship-provided password-protected PDF files.

## Modules

| Module | Practical | Status |
|---|---|---|
| PM1 | Password Cracking with JTR | Completed |
| PM2 | Password Cracking with NetworkWalks Tools | Completed |

## Objective

Understand and document the end-to-end password-auditing workflow for a protected PDF: extract a crackable PDF hash, supply it to an authorized password-auditing tool, perform a dictionary-based recovery exercise, and verify the recovered result against the protected file.

## Environment

| Component | Configuration |
|---|---|
| Operating System | Windows |
| John the Ripper | 1.9.0-jumbo-1, 64-bit Windows build |
| Johnny | 2.2 |
| JTR engine detected by Johnny | 1.9.0-jumbo-1 OMP [Cygwin 64-bit x86_64 AVX2 AC] |
| PM2 Hash Tool | NetworkWalks Hash Calculator |
| PM2 Cracking Tool | NetworkWalks Password Cracker |
| Training Material | Authorized protected PDF files supplied with the internship |

## Practical Workflow

The Week 3 workflow was executed in two ways.

### PM1

```text
Protected PDF
  → PDF hash extraction
  → $pdf$... representation
  → hash1.txt
  → Johnny
  → John the Ripper
  → recovered result
  → PDF verification
  → NetworkWalks flag
```

### PM2

```text
Protected PDF
  → NetworkWalks Hash Calculator
  → PDF mode
  → $pdf$... representation
  → NetworkWalks Password Cracker
  → built-in dictionary
  → recovered result
  → PDF verification
  → NetworkWalks flag
```

---

# PM1 — Password Cracking with JTR / Johnny

## Objective

Use John the Ripper and Johnny to recover the password of the authorized training PDF supplied for the lab.

## Execution

### 1. JTR preparation

The 64-bit Windows JTR package was extracted and the `run` directory was located. The main executable used for the practical was:

```text
john.exe
```

### 2. Johnny installation and configuration

Johnny 2.2 was opened and its JTR executable setting was configured to the extracted `john.exe`.

Johnny successfully detected:

```text
John the Ripper 1.9.0-jumbo-1 OMP
[Cygwin 64-bit x86_64 AVX2 AC]
```

This confirmed that the GUI was correctly connected to the JTR engine.

### 3. PDF hash extraction

A crackable PDF representation beginning with:

```text
$pdf$...
```

was extracted from the protected training PDF.

The complete extracted value was saved locally as:

```text
hash1.txt
```

The complete hash is intentionally not reproduced in this public repository.

### 4. Loading the hash

The `hash1.txt` file was loaded into Johnny. Johnny recognized the entry as **PDF** format.

### 5. Password recovery

The authorized cracking exercise was started.

Observed completion state:

```text
100%
1/1 cracked
0 left
format=PDF
```

The recovered training password displayed by Johnny was:

```text
password1
```

### 6. Verification

The recovered training password was used against the protected PDF. The file opened successfully and the NetworkWalks verification/flag screen was captured.

## PM1 Result Summary

| Item | Observed result |
|---|---|
| Input | Protected training PDF |
| Hash representation | $pdf$... |
| Local hash file | hash1.txt |
| JTR | 1.9.0-jumbo-1 |
| Johnny | 2.2 |
| Format detected | PDF |
| Completion | 100% |
| Cracked | 1/1 |
| Remaining | 0 |
| Verification | Successful |
| NetworkWalks flag | Captured |

## PM1 Evidence

[PM1 JTR / Johnny Evidence](./EVIDENCE/PM1-JTR-Johnny/)

Evidence included in the repository documents the JTR package, Johnny configuration, hash extraction, cracking completion, recovered result, PDF verification, and NetworkWalks flag.

---

# PM2 — Password Cracking with NetworkWalks Tools

## Objective

Use the NetworkWalks Hash Calculator and NetworkWalks Password Cracker to perform the browser-based password-recovery exercise against the authorized training PDF.

## Execution

### 1. Hash Calculator

The NetworkWalks Hash Calculator was opened and **PDF** mode was selected.

The primary file processed was:

```text
My-Locked-PDF1.pdf
```

The tool identified the PDF as encrypted and produced a crackable `$pdf$...` hash.

Visible parameters were:

| Parameter | Observed value |
|---|---|
| Revision | R4 |
| Version | V4 |
| Key length | 128 bit |

### 2. Password Cracker

The complete extracted PDF hash was supplied to the NetworkWalks Password Cracker.

The built-in candidate list contained:

```text
100 passwords
```

The attack produced:

```text
PASSWORD CRACKED SUCCESSFULLY
```

The recovered training password was:

```text
password1
```

At the visible success point, the interface showed approximately:

```text
Tried: 91 / 100
Speed: 9 p/s
Progress: 91%
```

### 3. Verification

The recovered training password was used to open the protected PDF successfully. The NetworkWalks verification/flag screen was captured.

## PM2 Result Summary

| Item | Observed result |
|---|---|
| Input | My-Locked-PDF1.pdf |
| Mode | PDF |
| Encryption | Detected |
| Revision | R4 |
| Version | V4 |
| Key length | 128 bit |
| Hash representation | $pdf$... |
| Candidate list | Built-in 100-password list |
| Successful match | password1 |
| Visible success point | 91/100 |
| Approx. displayed speed | 9 p/s |
| Verification | Successful |
| NetworkWalks flag | Captured |

## PM2 Evidence

[PM2 NetworkWalks Tools Evidence](./EVIDENCE/PM2-NetworkWalks-Tools/)

Evidence included in the repository documents the Hash Calculator, extracted hash, Password Cracker, dictionary progress, successful recovery, and verification screens.

---

# Additional Protected PDFs

During the practical session, two additional supplied training artifacts were also successfully opened using the recovered training password:

- `My-Locked-PDF2.pdf`
- `My-Locked-PDF3.pdf`

Each displayed a NetworkWalks congratulations/flag screen.

These results are documented as **supplementary observations**. The supplied PM1 and PM2 task material identifies **My Locked PDF1.pdf** as the named task file.

## Supplementary Evidence

The verification screenshots for PDF2 and PDF3 are stored with the PM2 evidence because they occurred during the same practical session.

---

# Technical Observations

## PDF hash representation

The protected PDF was converted into a crackable representation compatible with the password-auditing workflow. The visible representation begins with `$pdf$`.

## Dictionary-based recovery

The practical relied on candidate passwords from a dictionary rather than an unrestricted search of all possible strings. The supplied training password was present in the candidate set, allowing successful recovery.

## Verification matters

A cracking result was followed by opening the protected PDF. This distinguishes a candidate match from a verified working password.

## Tooling comparison

| Aspect | PM1 | PM2 |
|---|---|---|
| Interface | Johnny GUI | Web browser |
| Engine/tool | John the Ripper | NetworkWalks Password Cracker |
| Hash preparation | PDF hash extractor | NetworkWalks Hash Calculator |
| Candidate source | JTR workflow | Built-in 100-password list |
| Verification | PDF opened | PDF opened |
| Evidence | Screenshots | Screenshots |

---

# Security and Ethical Scope

This repository documents an authorized cybersecurity training exercise.

Password-recovery techniques are dual-use and must only be applied to:

- Files supplied for testing.
- Systems or accounts for which explicit authorization exists.
- Controlled educational or assessment environments.

Do not use the techniques against third-party documents, accounts, or systems without permission.

## Public repository precautions

This public repository intentionally excludes:

- Original protected PDF files.
- Complete reusable PDF hashes.
- API keys or access tokens.
- Unrelated private documents.
- Other sensitive credentials.

Screenshots should be reviewed before publication for accidental exposure of unrelated private information.

---

# Learning Outcomes

The Week 3 practical demonstrated:

- PDF password-protection concepts.
- PDF hash extraction.
- `$pdf$...` hash handling.
- John the Ripper setup on Windows.
- Johnny configuration and JTR detection.
- Dictionary-based password recovery.
- Interpretation of cracking progress and completion states.
- Verification of recovered passwords against the protected PDF.
- Use of browser-based password-auditing tools.
- Evidence collection and technical documentation.
- Responsible security-testing scope.

---

# Evidence Index

| Area | Repository location |
|---|---|
| PM1 visual evidence | [EVIDENCE/PM1-JTR-Johnny](./EVIDENCE/PM1-JTR-Johnny/) |
| PM2 visual evidence | [EVIDENCE/PM2-NetworkWalks-Tools](./EVIDENCE/PM2-NetworkWalks-Tools/) |
| PM1 documentation | [PM1-JTR-Johnny](./PM1-JTR-Johnny/) |
| PM2 documentation | [PM2-NetworkWalks-Tools](./PM2-NetworkWalks-Tools/) |
| Changelog | [CHANGELOG.md](./CHANGELOG.md) |
| Report area | [REPORT](./REPORT/) |

---

# Repository Structure

```text
NETWORKWALKS-AYUSH-B083-WK3-PASSWORD-CRACKING/
│
├── README.md
├── CHANGELOG.md
│
├── PM1-JTR-Johnny/
│   └── README.md
│
├── PM2-NetworkWalks-Tools/
│   └── README.md
│
├── EVIDENCE/
│   ├── README.md
│   ├── PM1-JTR-Johnny/
│   │   ├── PNG evidence
│   │   └── README.md
│   └── PM2-NetworkWalks-Tools/
│       ├── PNG evidence
│       └── README.md
│
└── REPORT/
    └── README.md
```

---

# Final Status

## PM1

- [x] JTR package prepared
- [x] Johnny installed
- [x] JTR executable configured
- [x] JTR engine detected
- [x] PDF hash extracted
- [x] `hash1.txt` prepared
- [x] Hash loaded into Johnny
- [x] PDF format recognized
- [x] Attack completed
- [x] 1/1 target cracked
- [x] Password verified against PDF
- [x] NetworkWalks flag captured

## PM2

- [x] Hash Calculator opened
- [x] PDF mode selected
- [x] Protected PDF processed
- [x] Crackable PDF hash extracted
- [x] Password Cracker opened
- [x] Hash supplied
- [x] Built-in dictionary used
- [x] Successful match obtained
- [x] Password verified against PDF
- [x] NetworkWalks flag captured

## Supplementary

- [x] PDF2 verification completed
- [x] PDF3 verification completed
- [x] Additional flag screens captured

**Week 3 practical work: COMPLETED.**

---

# Conclusion

Week 3 provided a complete practical introduction to password auditing against protected PDF training material.

The work progressed from hash extraction through password-candidate testing and finally to direct verification against the protected document. Using two different workflows also demonstrated the same underlying security concept through both a desktop toolchain and a browser-based toolchain.

The practical reinforces the defensive importance of strong and unique passwords and the requirement to keep password-auditing activity within an explicitly authorized scope.
