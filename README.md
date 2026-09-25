# NetworkWalks Week 3 — Password Cracking

![NetworkWalks](https://img.shields.io/badge/NetworkWalks-Week%203-blue)
![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-red)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Platform](https://img.shields.io/badge/Platform-Windows-0078D6)

This repository documents the practical cybersecurity work completed during **NetworkWalks Week 3**, focused on password auditing and password-recovery techniques against authorized, internship-provided password-protected PDF files.

The work covers two practical modules:

- **PM1 — Password Cracking with JTR**
- **PM2 — Password Cracking with NetworkWalks Tools**

The repository is intended to provide a reproducible record of the tools used, workflow followed, observations made, evidence collected, and security lessons learned.

> **Authorization and scope:** All password-recovery activity documented here was performed as part of an authorized cybersecurity training exercise. The techniques described must only be used against files, systems, or accounts for which explicit authorization has been granted.

---

## Table of Contents

- [Week 3 Overview](#week-3-overview)
- [Objectives](#objectives)
- [Environment](#environment)
- [Tools Used](#tools-used)
- [PM1 — JTR / Johnny](#pm1--jtr--johnny)
  - [PM1 Objective](#pm1-objective)
  - [PM1 Workflow](#pm1-workflow)
  - [JTR Configuration](#jtr-configuration)
  - [PDF Hash Extraction](#pdf-hash-extraction)
  - [Johnny Execution](#johnny-execution)
  - [PM1 Results](#pm1-results)
  - [PM1 Evidence](#pm1-evidence)
- [PM2 — NetworkWalks Tools](#pm2--networkwalks-tools)
  - [PM2 Objective](#pm2-objective)
  - [Hash Calculator](#hash-calculator)
  - [Password Cracker](#password-cracker)
  - [PM2 Results](#pm2-results)
  - [PM2 Evidence](#pm2-evidence)
- [Additional Protected PDFs](#additional-protected-pdfs)
- [Technical Observations](#technical-observations)
- [Security and Ethical Considerations](#security-and-ethical-considerations)
- [Learning Outcomes](#learning-outcomes)
- [Evidence Organization](#evidence-organization)
- [Repository Structure](#repository-structure)
- [Limitations and Notes](#limitations-and-notes)
- [Final Status](#final-status)

---

## Week 3 Overview

The Week 3 practical exercise demonstrated a complete password-auditing workflow for protected PDF documents.

The workflow consisted of:

1. Identifying a password-protected PDF.
2. Extracting the PDF's crackable hash representation.
3. Preserving the complete hash in a text file for JTR-based testing.
4. Configuring Johnny to use the John the Ripper engine.
5. Loading the extracted PDF hash into Johnny.
6. Running the authorized dictionary-based password-recovery exercise.
7. Verifying the recovered training password against the protected PDF.
8. Repeating the hash-to-recovery workflow using the NetworkWalks web tools.
9. Capturing the resulting NetworkWalks verification/flag screens.
10. Organizing the practical evidence for internship submission.

This demonstrates the difference between **password hashing/encryption artifacts** and the actual password: the auditing tool works against a crackable representation rather than directly reading the protected document's password.

---

## Objectives

The main objectives of Week 3 were:

- Understand the practical password-auditing workflow.
- Learn how password-protected PDF files can expose a crackable hash representation.
- Extract and preserve a PDF hash in the format expected by password-auditing software.
- Configure **John the Ripper** through the **Johnny** graphical interface.
- Identify the correct hash format automatically recognized by JTR.
- Perform an authorized dictionary-based recovery attempt.
- Understand attack progress, completion status, and recovered results.
- Validate a recovered password by opening the original protected PDF.
- Use NetworkWalks' browser-based Hash Calculator and Password Cracker.
- Record screenshots and other evidence suitable for a cybersecurity internship submission.
- Understand the defensive importance of strong, unique passwords.

---

## Environment

| Component | Configuration |
|---|---|
| Operating System | Windows |
| JTR Build | John the Ripper **1.9.0-jumbo-1** |
| JTR Architecture | 64-bit Windows |
| Johnny | **2.2** |
| JTR Engine Detected by Johnny | **1.9.0-jumbo-1 OMP [Cygwin 64-bit x86_64 AVX2 AC]** |
| PM2 Hash Tool | NetworkWalks Hash Calculator |
| PM2 Cracking Tool | NetworkWalks Password Cracker |
| Training Material | Authorized password-protected PDF files |

---

## Tools Used

### 1. John the Ripper

John the Ripper (JTR) was used as the password-auditing engine for PM1.

The Week 3 setup used the **1.9.0-jumbo-1** Windows build. Johnny was configured to point to the JTR executable located inside the JTR `run` directory.

### 2. Johnny

Johnny provided the graphical interface used to configure and operate John the Ripper.

The GUI was used to:

- Configure the JTR executable.
- Verify JTR detection.
- Load the password/hash input.
- Identify the PDF hash format.
- Start the attack.
- Monitor progress.
- Confirm completion and cracking status.

### 3. NetworkWalks Hash Calculator

The NetworkWalks Hash Calculator was used in **PDF** mode to process the protected PDF and extract a crackable `$pdf$...` representation.

### 4. NetworkWalks Password Cracker

The NetworkWalks Password Cracker was used to perform the authorized dictionary-based recovery exercise using the extracted PDF hash.

---

# PM1 — JTR / Johnny

## PM1 Objective

The objective of PM1 was to understand and execute a complete John the Ripper workflow against an authorized password-protected PDF.

The practical chain was:

```text
Protected PDF
      |
      v
PDF hash extraction
      |
      v
$pdf$... hash
      |
      v
hash1.txt
      |
      v
Johnny GUI
      |
      v
John the Ripper engine
      |
      v
Dictionary-based recovery
      |
      v
Recovered training password
      |
      v
PDF verification
      |
      v
NetworkWalks verification flag
```

---

## PM1 Workflow

### Step 1 — JTR Package

The Windows JTR package was extracted and the `run` directory was located.

The primary executable used by Johnny was:

```text
john.exe
```

### Step 2 — Johnny Configuration

Johnny was installed and opened.

Under Johnny's settings, the JTR executable path was configured to point to the extracted `john.exe`.

Johnny then detected:

```text
John the Ripper 1.9.0-jumbo-1 OMP
[Cygwin 64-bit x86_64 AVX2 AC]
```

This confirmed that Johnny was successfully connected to the JTR engine.

### Step 3 — PDF Hash Extraction

The protected training PDF was processed with a PDF hash-extraction utility.

The resulting value used the PDF password-hash format:

```text
$pdf$...
```

The complete extracted value was preserved in:

```text
hash1.txt
```

The actual hash is intentionally not reproduced in this README because this repository is public and publishing unnecessary credential-recovery material is not required for documenting the exercise.

### Step 4 — Loading the Hash

The extracted hash file was loaded into Johnny.

Johnny recognized the entry as:

```text
PDF
```

This confirmed that the extracted hash was being interpreted using the expected PDF format.

### Step 5 — Running the Attack

The authorized dictionary-based recovery exercise was started from Johnny.

The attack progressed until completion.

Final observed state:

```text
100%
1/1 cracked
0 left
format=PDF
```

### Step 6 — Password Verification

The recovered training password was used to open the protected PDF.

The PDF opened successfully, confirming that the recovered credential was valid for the training document.

A NetworkWalks congratulations/verification page was then captured as evidence.

---

## JTR Configuration

The important configuration points verified during the practical were:

- Windows 64-bit JTR package.
- Johnny version 2.2.
- JTR executable located under the extracted `run` directory.
- Johnny successfully detected the JTR engine.
- PDF hash recognized as **PDF** format.
- Attack completed successfully.
- Final status showed **1/1 cracked, 0 left**.

---

## PM1 Results

### Result Summary

| Item | Result |
|---|---|
| Hash type | PDF |
| Hash representation | `$pdf$...` |
| Input file | `hash1.txt` |
| JTR version | 1.9.0-jumbo-1 |
| Johnny version | 2.2 |
| Attack completion | 100% |
| Cracked | 1 |
| Remaining | 0 |
| PDF verification | Successful |
| NetworkWalks flag | Captured |

The observed training password recovered during the exercise was:

```text
password1
```

Because this is a deliberately supplied training credential, it is recorded here as an observed lab result rather than as a real-world credential.

---

## PM1 Evidence

Recommended evidence sequence:

1. JTR package extracted.
2. JTR `run` directory visible.
3. Johnny installation/interface.
4. Johnny JTR executable configuration.
5. JTR version detection.
6. PDF hash extraction.
7. `hash1.txt` containing the extracted hash.
8. Hash loaded into Johnny.
9. PDF format recognition.
10. JTR attack in progress.
11. Attack completion showing 100%.
12. Result showing 1/1 cracked and 0 left.
13. Protected PDF opened with recovered password.
14. NetworkWalks verification/flag screen.

Evidence screenshots should be placed under the appropriate PM1 evidence directory.

---

# PM2 — NetworkWalks Tools

## PM2 Objective

PM2 repeated the password-recovery workflow using the NetworkWalks browser-based tools.

The practical chain was:

```text
Protected PDF
      |
      v
NetworkWalks Hash Calculator
      |
      v
PDF mode
      |
      v
$pdf$... hash
      |
      v
NetworkWalks Password Cracker
      |
      v
Built-in dictionary
      |
      v
Recovered password
      |
      v
PDF verification
      |
      v
NetworkWalks flag
```

---

## Hash Calculator

The NetworkWalks Hash Calculator was opened and the **PDF** tab was selected.

The protected training file processed during the main PM2 workflow was:

```text
My-Locked-PDF1.pdf
```

The tool identified the document as encrypted and generated a crackable PDF hash.

The visible PDF parameters were:

| Parameter | Observed value |
|---|---|
| Revision | R4 |
| Version | V4 |
| Key length | 128 bit |
| Output type | `$pdf$...` compatible hash |

The complete generated hash was then copied for use in the password-cracking stage.

---

## Password Cracker

The NetworkWalks Password Cracker was opened after hash extraction.

The extracted PDF hash was pasted into the PDF hash field.

The tool provided a built-in dictionary containing:

```text
100 passwords
```

The cracking process was started.

The visible successful result showed:

```text
PASSWORD CRACKED SUCCESSFULLY
```

The successful training password was:

```text
password1
```

At the visible success point, the interface showed approximately:

```text
Tried: 91 / 100
Speed: 9 p/s
Progress: 91%
```

The protected PDF was subsequently opened using the recovered password.

---

## PM2 Results

| Item | Observed result |
|---|---|
| Input | `My-Locked-PDF1.pdf` |
| Mode | PDF |
| Encryption | Detected |
| Revision | R4 |
| Version | V4 |
| Key length | 128 bit |
| Hash format | `$pdf$...` |
| Dictionary | Built-in 100-password list |
| Successful match | `password1` |
| Visible progress at success | 91/100 |
| Approx. speed shown | 9 p/s |
| PDF verification | Successful |
| NetworkWalks flag | Captured |

---

## PM2 Evidence

Recommended evidence sequence:

1. NetworkWalks Hash Calculator.
2. PDF mode selected.
3. Protected PDF selected.
4. Encrypted-PDF detection.
5. Extracted `$pdf$...` hash.
6. PDF parameters displayed by the tool.
7. NetworkWalks Password Cracker.
8. Extracted hash supplied to the cracker.
9. Built-in 100-password list selected/active.
10. Attack progress.
11. Successful password match.
12. Protected PDF opened.
13. NetworkWalks congratulations/flag screen.

---

# Additional Protected PDFs

During the practical session, two additional supplied training PDFs were also tested:

- `My-Locked-PDF2.pdf`
- `My-Locked-PDF3.pdf`

The recovered training password was successfully used to open these supplied training artifacts, and NetworkWalks congratulations/flag screens were displayed.

These results are retained as **supplementary practical observations**.

They should not be confused with the primary task file. The supplied PM1/PM2 task material identifies **My Locked PDF1.pdf** as the named task file, while PDF2 and PDF3 were additionally verified during the practical session.

---

# Technical Observations

## 1. PDF Hash Extraction

A password-protected PDF does not require the password itself to be directly supplied to JTR. A crackable representation can first be extracted from the protected document.

The extracted representation used in this practical followed the:

```text
$pdf$...
```

format.

This value was then supplied to the password-auditing workflow.

## 2. Hash Format Recognition

Johnny correctly identified the loaded input as **PDF** format.

This is important because password-auditing tools support multiple hash formats, and the correct format determines how candidate passwords are tested.

## 3. Dictionary-Based Recovery

Both practical workflows used a dictionary-based approach.

Rather than generating arbitrary candidates indefinitely, the exercise tested candidate passwords from an available wordlist/dictionary.

The supplied training password appeared in the permitted candidate list, resulting in successful recovery.

## 4. Verification

The cracking result was not treated as complete until the recovered password was used against the actual protected PDF.

This provided an additional validation step:

```text
Recovered candidate
       |
       v
Open protected PDF
       |
       v
Successful decryption
       |
       v
Training result confirmed
```

## 5. Evidence Collection

The practical was documented through screenshots showing:

- Tool configuration.
- Hash extraction.
- Hash loading.
- Attack progress.
- Successful recovery.
- PDF verification.
- NetworkWalks flag pages.

This creates an evidence trail from initial setup through final verification.

---

# Security and Ethical Considerations

Password-recovery tools are dual-use cybersecurity tools.

The same workflow used in a controlled training laboratory can be misused against documents or accounts without authorization.

Therefore:

- Only test files explicitly provided or authorized for testing.
- Do not attack third-party accounts or systems.
- Do not publish private credentials or authentication secrets.
- Do not upload protected source PDFs unnecessarily.
- Do not publish complete password hashes when they are not required for demonstrating the work.
- Keep API keys, access tokens, personal documents, and unrelated private information out of the repository.
- Preserve evidence in a way that demonstrates the technique without exposing unnecessary sensitive material.

The practical documented in this repository was conducted within the scope of the NetworkWalks cybersecurity training exercise.

---

# Learning Outcomes

By completing Week 3, the following practical skills were demonstrated:

### Password Auditing

- Understanding of password-recovery workflows.
- Understanding of dictionary-based attacks.
- Understanding of candidate-password testing.

### PDF Security

- Recognition of password-protected PDFs.
- Extraction of a crackable PDF representation.
- Understanding of the `$pdf$...` hash format.
- Verification of a recovered password against the protected document.

### John the Ripper

- Installation/setup of the Windows JTR package.
- Identification of the JTR `run` directory.
- Configuration of Johnny to use `john.exe`.
- Verification of JTR version detection.
- Loading a PDF hash.
- Monitoring an attack.
- Interpreting completion status.

### NetworkWalks Tools

- Using the PDF mode of the Hash Calculator.
- Extracting a crackable PDF hash.
- Supplying the hash to the Password Cracker.
- Using the built-in dictionary.
- Interpreting attack progress and success output.

### Cybersecurity Documentation

- Capturing reproducible screenshots.
- Recording tool versions and observed results.
- Separating primary task evidence from supplementary observations.
- Organizing evidence for internship submission.
- Applying responsible disclosure and authorization principles.

---

# Evidence Organization

Evidence should be organized according to the practical module.

Recommended structure:

```text
EVIDENCE/
├── PM1-JTR-Johnny/
│   ├── 01-jtr-package.png
│   ├── 02-johnny-configuration.png
│   ├── 03-jtr-detected.png
│   ├── 04-pdf-hash-extraction.png
│   ├── 05-hash-loaded.png
│   ├── 06-jtr-progress.png
│   ├── 07-jtr-completed.png
│   ├── 08-pdf-verification.png
│   └── 09-networkwalks-flag.png
│
└── PM2-NetworkWalks-Tools/
    ├── 01-hash-calculator.png
    ├── 02-pdf-selected.png
    ├── 03-pdf-hash.png
    ├── 04-password-cracker.png
    ├── 05-cracking-progress.png
    ├── 06-success.png
    ├── 07-pdf-verification.png
    └── 08-networkwalks-flag.png
```

Additional PDF2/PDF3 screenshots can be stored separately and clearly labeled as supplementary evidence.

---

# Repository Structure

The repository is organized as follows:

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
│   └── README.md
│
└── REPORT/
    └── README.md
```

The structure is intentionally separated into:

- Practical-module documentation.
- Evidence.
- Report material.
- Repository-level project documentation.

---

# Limitations and Notes

## Training Environment

The results documented here were obtained against the supplied NetworkWalks training material.

They should not be interpreted as representative of all PDF encryption configurations or password-security scenarios.

## Dictionary Dependence

A dictionary attack can succeed quickly when the target password is present in the tested candidate list.

Failure to recover a password from a limited dictionary does not prove that the password is strong; it only means that the tested candidate set did not produce a successful match.

## Public Repository

This repository is intended to document the cybersecurity learning process.

For that reason:

- Full protected PDF files are not required.
- Complete reusable hashes should not be published unnecessarily.
- Sensitive credentials should not be added.
- Screenshots should be reviewed before upload to ensure they contain no unrelated private information.

## Evidence Accuracy

Only results actually observed during the practical session are documented.

No fabricated performance measurements, timings, attack results, or tool outputs should be added to the final submission.

---

# Final Status

## Week 3 Practical Status

**COMPLETED**

### PM1

- [x] JTR package prepared
- [x] Johnny configured
- [x] JTR engine detected
- [x] PDF hash extracted
- [x] Hash loaded into Johnny
- [x] PDF format recognized
- [x] Attack completed
- [x] 1/1 target cracked
- [x] Protected PDF verified
- [x] NetworkWalks flag captured

### PM2

- [x] NetworkWalks Hash Calculator opened
- [x] PDF mode selected
- [x] Protected PDF processed
- [x] Crackable PDF hash extracted
- [x] NetworkWalks Password Cracker opened
- [x] Hash supplied
- [x] Built-in dictionary used
- [x] Password recovered
- [x] Protected PDF verified
- [x] NetworkWalks flag captured

### Supplementary Work

- [x] My-Locked-PDF2.pdf verified
- [x] My-Locked-PDF3.pdf verified
- [x] Additional NetworkWalks flag screens captured

---

## Conclusion

Week 3 provided practical exposure to the end-to-end password-auditing lifecycle:

```text
Identify protected document
        ↓
Extract crackable representation
        ↓
Select compatible password-auditing workflow
        ↓
Test authorized candidate passwords
        ↓
Interpret cracking results
        ↓
Verify recovered password
        ↓
Document evidence
```

The exercise demonstrated that password security depends significantly on password complexity and resistance to common candidate lists. It also reinforced an important cybersecurity principle: password-recovery tools must be used only within an explicitly authorized scope.

---

## Repository Maintenance

Future additions should preserve the same documentation standard:

- Keep PM1 and PM2 evidence separate.
- Use descriptive evidence filenames.
- Record only verified results.
- Keep sensitive material out of the public repository.
- Update `CHANGELOG.md` whenever significant Week 3 artifacts are added.
- Place the final internship report in the `REPORT/` directory.
