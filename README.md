# NetworkWalks B083 — Week 3 · Password Cracking

<p align="center">
  <img src="https://img.shields.io/badge/purpose-educational%20only-blue" alt="Educational">
  <img src="https://img.shields.io/badge/testing-authorized-success" alt="Authorized">
  <img src="https://img.shields.io/badge/tool-John%20the%20Ripper-red" alt="John the Ripper">
  <img src="https://img.shields.io/badge/tool-Johnny%20GUI-orange" alt="Johnny">
  <img src="https://img.shields.io/badge/tool-NetworkWalks%20Online%20Tools-purple" alt="NetworkWalks Tools">
  <img src="https://img.shields.io/badge/NetworkWalks-Week%203-red" alt="Week 3">
</p>

This repository documents **Week 3** of my Cybersecurity & Ethical Hacking internship with NetworkWalks Academy (Batch B083). Week 3 focuses on **password cracking** — recovering the passwords of encrypted PDF files and confirming the results by unlocking and reading them. It consists of two parts using different toolsets to achieve the same objective:

- **Module 1 — Password Cracking with JTR:** Using **John the Ripper (JTR)** alongside its graphical front-end **Johnny** — industry-standard tools for credential recovery.
- **Module 2 — Password Cracking with NetworkWalks Tools:** Using NetworkWalks' native browser-based **Hash Calculator** and **Password Cracker** for a lightweight, installation-free approach.

Both modules follow a unified methodology: extracting the password hash from a locked PDF file and conducting a dictionary attack to match the key. This demonstrates that both professional CLI utilities and web tools rely on the **exact same core cryptographic principles** — and that weak passwords can be compromised in seconds.

---

## ⚠️ Authorization & Scope

All files processed in this lab are **authorized practice PDFs provided by NetworkWalks** as part of the B083 internship curriculum, specifically designed as safe training (Capture The Flag / CTF) exercises.

**In scope:**
- Course-provided practice PDFs (`My Locked PDF1.pdf`, `PDF2`, `PDF3`), analyzed strictly on my local lab environment.

No external files, third-party systems, or unauthorized assets were targeted or tested.

---

## Module 1 · Password Cracking with John the Ripper (JTR)

**John the Ripper (JTR)** is a powerful command-line password recovery tool, and **Johnny** serves as its intuitive point-and-click GUI wrapper. The goal of this module was to recover passwords for three locked practice PDFs.

### Tools Used
- **John the Ripper (jumbo)** — CLI password security auditing and recovery tool
- **Johnny** — Graphical front-end for JTR
- **Online PDF Hash Extractor** — https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php

### Execution Steps

1. **Set up and verify John (CLI):** Installed and validated the snap package version of JTR.
2. **Launch Johnny (GUI):** Configured Johnny to reference the valid JTR executable backend, confirming version `1.9.0-jumbo` was active.
3. **Extract the PDF Password Hash:** Uploaded each locked PDF to the online extractor to yield the required hash format starting with `$pdf$`. Saved outputs to dedicated files (`hash1.txt`, `hash2.txt`, `hash3.txt`).
4. **Execute the Attack:** Loaded the hash files into Johnny (*Open password file → Start new attack*).
   - PDF 1 recovered -> `password1`
   - PDF 2 recovered -> `password1`
   - PDF 3 recovered -> `1qaz2wsx`
5. **Verify Results:** Successfully opened all target PDFs using the recovered credentials.

### Results — Module 1

| PDF File | Recovered Password | Vulnerability Analysis |
| :--- | :--- | :--- |
| `My Locked PDF1.pdf` | `password1` | Highly common default credential |
| `My Locked PDF2.pdf` | `password1` | Highly common default credential |
| `My Locked PDF3.pdf` | `1qaz2wsx` | Standard keyboard-walk pattern |



<p align="center">
<img width="1366" height="768" alt="1" src="https://github.com/user-attachments/assets/01a94b55-b016-4748-8003-a6ed97e32608" />
<img width="1366" height="768" alt="2" src="https://github.com/user-attachments/assets/2f6cae95-1a3d-4fa6-8a23-ccb271c408de" />
<img width="1366" height="768" alt="3" src="https://github.com/user-attachments/assets/bcb40302-49ab-455a-b3dc-f10d4dc8b9e3" />
<img width="1366" height="768" alt="4" src="https://github.com/user-attachments/assets/12dda5b9-2b7c-472c-93aa-ebc75ab9101c" />
<img width="1366" height="768" alt="5" src="https://github.com/user-attachments/assets/e28c7be4-f3a1-4b25-b554-03f4d1abdbbc" />
<img width="1366" height="768" alt="6" src="https://github.com/user-attachments/assets/bbf62989-ce1f-43df-9a6c-5603f27f28d8" />
<img width="1366" height="768" alt="7" src="https://github.com/user-attachments/assets/b026cf84-ea66-4c1e-a926-aff1655636b7" />
<img width="1366" height="768" alt="8" src="https://github.com/user-attachments/assets/85098a16-eadd-4242-b071-8ac1d7f17a85" />
<img width="1366" height="768" alt="9" src="https://github.com/user-attachments/assets/d9d5e0fe-63e4-4256-a80e-350b11d3734e" />
<img width="1366" height="768" alt="10" src="https://github.com/user-attachments/assets/0db32566-d803-417f-ad9f-140af85192df" />




</p>

---

## Module 2 · Password Cracking with NetworkWalks Online Tools

This module achieves the same security audit objectives using NetworkWalks' **browser-based utility suite**, highlighting how web applications execute underlying dictionary attacks.

### Tools Used
- **[NetworkWalks Hash Calculator](https://networkwalks.com/hash-calculator/)** — Extracts the crackable `$pdf$` hash directly within the browser client-side.
- **[NetworkWalks Password Cracker](https://networkwalks.com/password-cracker/)** — Conducts automated dictionary matching against the targeted hash string.

### Execution Steps

1. **Access Lab Task:** Downloaded the targeted practice files from the portal.
2. **Hash Extraction:** Uploaded the locked PDF into the Hash Calculator's **PDF** tab to parse encryption parameters (Revision R4, Version V4, 128-bit key) and output the `$pdf$` hash.
3. **Dictionary Attack:** Pasted the extracted hash into the Password Cracker tool to test against integrated dictionary wordlists.
4. **Verification:** Successfully unlocked the PDF file using the discovered password string.

### Results — Module 2

| PDF File | Recovered Password | Attack Method |
| :--- | :--- | :--- |
| `My Locked PDF1.pdf` | `password1` | Dictionary attack via built-in wordlist |
| `My Locked PDF2.pdf` | `password1` | Dictionary attack via built-in wordlist |
| `My Locked PDF3.pdf` | `1qaz2wsx` | Dictionary attack via built-in wordlist |

<p align="center">

<img width="1366" height="768" alt="11" src="https://github.com/user-attachments/assets/a1d0b985-8163-4585-92fa-d23f5ed467bc" />
<img width="1366" height="768" alt="12" src="https://github.com/user-attachments/assets/24753d75-1f27-4360-aed0-07fbc27f519a" />
<img width="1366" height="768" alt="13" src="https://github.com/user-attachments/assets/dda3404f-0c8b-4437-b2d5-235585e02290" />
<img width="1366" height="768" alt="14" src="https://github.com/user-attachments/assets/0c521638-04d9-421b-bb88-bb7e1fd0e3b2" />
</p>

---

### Author

**Muhammad Umar** | NetworkWalks — Cybersecurity Internship | Week 3 | Batch B083
