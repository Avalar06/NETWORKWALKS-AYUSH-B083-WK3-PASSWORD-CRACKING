# PM1 — Password Cracking with JTR and Johnny

## Objective

Recover the password of the protected training PDF using John the Ripper (JTR) and Johnny.

## Tools

- John the Ripper 1.9.0-jumbo-1 64-bit Windows
- Johnny 2.2
- PDF hash extraction utility
- Windows

## Procedure

1. Extract the JTR Windows package.
2. Locate `run\\john.exe`.
3. Install Johnny.
4. Open Johnny Settings and browse to the JTR `john.exe`.
5. Confirm Johnny detects the JTR installation.
6. Extract the protected PDF's crackable `$pdf$...` hash.
7. Save the complete hash as `hash1.txt`.
8. Load `hash1.txt` into Johnny.
9. Confirm the entry is recognized as PDF format.
10. Start the new attack.
11. Wait for completion.
12. Record the recovered result.
13. Open the protected PDF with the recovered password.
14. Capture the NetworkWalks verification flag.

## Observed Result

- Johnny detected **John the Ripper 1.9.0-jumbo-1 OMP [Cygwin 64-bit x86_64 AVX2 AC]**.
- The entry was recognized as **PDF** format.
- The attack reached **100%**.
- Johnny reported **1/1 cracked, 0 left**.
- Recovered training password: **password1**.
- PDF verification succeeded.
- NetworkWalks verification flag was captured.

## Evidence Sequence

Store screenshots under `evidence/` and/or the top-level `EVIDENCE/PM1-JTR-Johnny/` directory.

Recommended evidence:
1. JTR package and `john.exe`
2. Johnny installation
3. Johnny JTR executable configuration
4. PDF hash extraction
5. `hash1.txt`
6. Hash loaded in Johnny
7. Completed JTR attack
8. Recovered result
9. Opened PDF / verification flag

## Source

Official NetworkWalks Week 3 — Project Module 1: **Password Cracking with JTR**.
