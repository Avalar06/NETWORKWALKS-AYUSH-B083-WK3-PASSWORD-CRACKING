# PM2 — Password Cracking with NetworkWalks Tools

## Objective

Recover the password of the protected training PDF using the NetworkWalks Hash Calculator and NetworkWalks Password Cracker.

## Tools

- NetworkWalks Hash Calculator
- NetworkWalks Password Cracker
- Web browser
- Windows

## Procedure

1. Open the NetworkWalks Hash Calculator.
2. Select **PDF** mode.
3. Process the protected PDF.
4. Confirm that the PDF is encrypted and a crackable `$pdf$...` hash is produced.
5. Copy the complete hash.
6. Open the NetworkWalks Password Cracker.
7. Paste the hash into the PDF hash field.
8. Use the available built-in dictionary for the training task.
9. Start the cracking process.
10. Record the successful match and visible attack statistics.
11. Open the protected PDF with the recovered password.
12. Capture the verification evidence.

## Observed Result

- PDF hash extraction succeeded.
- The tool identified the file as encrypted.
- Reported parameters: **Revision R4, Version V4, Key length 128 bit**.
- Built-in list: **100 passwords**.
- Successful match: **password1**.
- Visible success point: **91/100 tried**, approximately **9 p/s**.
- Protected PDF verification succeeded.

## Additional PDFs

The supplied `My-Locked-PDF2.pdf` and `My-Locked-PDF3.pdf` were also opened successfully during the practical session and displayed NetworkWalks flag screens. These are documented as supplementary observations, not as replacements for the named PM2 task file.

## Evidence Sequence

1. Hash Calculator — PDF mode
2. PDF selected/processed
3. Extracted `$pdf$...` hash
4. Password Cracker with hash
5. Cracking progress
6. Successful match
7. PDF verification / flag

## Source

Official NetworkWalks Week 3 — Project Module 2: **Password Cracking with NetworkWalks Tools**.
