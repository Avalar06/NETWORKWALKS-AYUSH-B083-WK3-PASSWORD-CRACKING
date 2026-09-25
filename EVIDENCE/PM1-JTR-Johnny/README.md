# PM1 — JTR / Johnny Evidence

This folder contains the actual PNG evidence captured during the Week 3 PM1 practical execution. The screenshots have already been uploaded and should be treated as the primary visual evidence for the JTR workflow.

## Evidence Summary

| File | What it documents |
|---|---|
| `01-jtr-package.png` | John the Ripper Windows package / installation source used for the lab. |
| `02-johnny-interface.png` | Johnny graphical interface after installation. |
| `03-johnny-jtr-configuration.png` | Johnny Settings showing the configured JTR `john.exe` path. |
| `04-pdf-hash-extraction.png` | Extraction of the protected PDF's crackable `$pdf$...` hash. |
| `05-jtr-attack-complete.png` | Completed JTR execution and cracking state. |
| `06-recovered-result.png` | Johnny Passwords view showing the recovered training result and PDF format. |
| `07-pdf-verification-flag.png` | Final protected-PDF verification and NetworkWalks flag capture. |

## Execution Evidence Chain

The PNG sequence demonstrates the practical chain:

```text
JTR package
   ↓
Johnny GUI
   ↓
john.exe configured
   ↓
PDF hash extracted
   ↓
JTR attack executed
   ↓
Password recovered
   ↓
Protected PDF verified
   ↓
NetworkWalks flag captured
```

## Result Confirmed

The uploaded screenshots document that:

- Johnny was successfully connected to the JTR engine.
- The protected PDF hash was accepted as **PDF** format.
- The JTR run completed successfully.
- The final state showed **1/1 cracked, 0 left**.
- The recovered training password was displayed in Johnny.
- The protected PDF opened successfully.
- The NetworkWalks verification/flag screen was captured.

## Evidence Handling

These PNG files are the visual record of the practical work. Keep them unchanged where possible so the evidence remains faithful to the original execution.

Do not add unrelated screenshots, private credentials, API tokens, or personal documents to this folder.

## Note

The repository intentionally does not include the original protected PDF or the complete reusable PDF hash. The screenshots provide the required evidence without unnecessarily publishing sensitive training artifacts.
