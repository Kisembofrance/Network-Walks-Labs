# 🔐 PASSWORD CRACKING & HASH AUDITING REPORT

**Cryptographic Hash Extraction & Dictionary Attack Analysis**  
**WEEK 3 | MODULES 1 & 2 | CYBERSECURITY | NETWORKWALKS**

| Field | Detail |
| :--- | :--- |
| **Analyst** | France Kisembo |
| **Tools Used** | John the Ripper (JTR 1.9.0 Jumbo), Johnny GUI, Networkwalks Hash Calculator & Password Cracker |
| **Target Files** | 3 Password-Protected PDF Documents (`My Locked PDF1.pdf` + 2 additional lab PDFs) |
| **Status** | Completed (3/3 Hashes Cracked – 100%) |

---

## 1. Objective
Extract `$pdf$` cryptographic hashes from multiple password-protected PDF files and execute dictionary and rule-based attacks using both local desktop tools (John the Ripper / Johnny) and browser-based utilities (Networkwalks Tools) to audit password strength.

---

## 2. Methodology
1. **Hash Extraction:** Used `pdf2john` / online hash extractors and the Networkwalks Hash Calculator to convert encrypted PDF metadata into crackable `$pdf$4*4*128...` hash strings saved in `hash1.txt`.
2. **Local Cracking (Module 1):** Linked `john.exe` inside the **Johnny GUI** on Windows, loaded the extracted hashes, and ran an automated attack session.
3. **Browser Cracking (Module 2):** Verified hash recovery using the **Networkwalks Password Cracker** dictionary attack tool.
4. **Verification:** Unlocked all three protected PDF documents using the recovered passwords and captured the completion flags.

---

## 3. Cracked Password Results

| Target | Hash Format | Recovered Password | Vulnerability / Pattern |
| :--- | :--- | :--- | :--- |
| **PDF #1** | `$pdf$4*4*128...` | `good-luck` | Common dictionary phrase |
| **PDF #2** | `$pdf$4*4*128...` | `password1` | Dictionary word + single digit |
| **PDF #3** | `$pdf$4*4*128...` | `1qaz2wsx` | Predictable keyboard walk pattern |

---

## 4. Key Security Recommendations
* **Avoid Keyboard Walks & Common Words:** Patterns like `1qaz2wsx` and `password1` are included in standard cracking wordlists and fall within seconds.
* **Enforce High Entropy:** Use randomly generated passphrases of at least **12–16 characters** mixing uppercase, lowercase, numbers, and symbols.
