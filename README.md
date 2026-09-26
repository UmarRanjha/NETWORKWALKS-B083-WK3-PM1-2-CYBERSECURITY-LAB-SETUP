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
  <img width="289" height="112" alt="1" src="https://github.com/user-attachments/assets/a9780f15-94a5-4556-aa57-afd1f38bf713" />
  <img width="646" height="389" alt="Screenshot 2" src="https://github.com/user-attachments/assets/c00fbe09-9abe-4d8c-a259-22eac55fd1dd" />
</p>

<p align="center">
  <img width="953" height="410" alt="Screenshot 3" src="https://github.com/user-attachments/assets/3fdd0201-b9f9-49f1-a682-460a48256e50" />
  <img width="919" height="388" alt="Screenshot 4" src="https://github.com/user-attachments/assets/9c713432-835f-4e00-ae8c-b529ad6af1a2" />
  <img width="644" height="395" alt="Screenshot 5" src="https://github.com/user-attachments/assets/117dd328-dcf1-426a-9660-dd5e0b79fb53" />
  <img width="945" height="378" alt="Screenshot 6" src="https://github.com/user-attachments/assets/b51e544d-2d00-4b8c-8df4-29be6ffae0c0" />
  <img width="911" height="385" alt="Screenshot 7" src="https://github.com/user-attachments/assets/b08c9650-7a25-4ebb-b176-0801f146c836" />
  <img width="638" height="392" alt="Screenshot 8" src="https://github.com/user-attachments/assets/d8fa4e20-0cbf-4d5c-a4bc-03379a61f264" />
  <img width="958" height="391" alt="Screenshot 9" src="https://github.com/user-attachments/assets/ad552add-962d-480c-b23e-f16d69fd6ec3" />
  <img width="943" height="395" alt="Screenshot 10" src="https://github.com/user-attachments/assets/a0a6de29-9746-4cf1-a828-b96422769cc8" />
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
  <img width="925" height="393" alt="Screenshot 11" src="https://github.com/user-attachments/assets/f4c08380-24a2-4558-bcba-318d545dcff7" />
  <img width="932" height="390" alt="Screenshot 12" src="https://github.com/user-attachments/assets/4d4defa6-949a-47b8-8ffb-5a40aeacf4ad" />
  <img width="917" height="389" alt="Screenshot 13" src="https://github.com/user-attachments/assets/5024b3f5-9ec1-4775-a6f0-8e571520f1dc" />
  <img width="904" height="338" alt="Screenshot 14" src="https://github.com/user-attachments/assets/c6b35fcf-9b19-47e2-84ee-81fd51e65af2" />
  <img width="803" height="398" alt="Screenshot 15" src="https://github.com/user-attachments/assets/768b82e9-f181-4e78-93ab-b22882edd87c" />
  <img width="949" height="396" alt="Screenshot 16" src="https://github.com/user-attachments/assets/a063e9b6-f377-4faf-b4bc-0cfc5e7d896a" />
  <img width="900" height="401" alt="Screenshot 17" src="https://github.com/user-attachments/assets/8ff49b8c-ad88-4f75-abaf-63c56acdd0dc" />
  <img width="932" height="346" alt="Screenshot 18" src="https://github.com/user-attachments/assets/69e078a0-b5f2-43c9-8dc4-851051639e4f" />
  <img width="930" height="396" alt="Screenshot 19" src="https://github.com/user-attachments/assets/4903310e-9fe2-45cc-b1e0-e5f1c77884fc" />
</p>

---

### Author

**Muhammad Umar** | NetworkWalks — Cybersecurity Internship | Week 3 | Batch B083
