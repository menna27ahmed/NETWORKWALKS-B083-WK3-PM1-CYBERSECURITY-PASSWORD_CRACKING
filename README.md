# Password Cracking Labs — Cybersecurity & Ethical Hacking (Week 3)

This repo documents two completed lab tasks from the NetworkWalks Cybersecurity & Ethical Hacking training program, both focused on recovering the password of a locked PDF file (`My Locked PDF1.pdf`).

## Background

Password cracking is the process of recovering a password from stored data or a protected file. Security professionals use it to test password strength and demonstrate why weak passwords are risky.

When a file such as a PDF, ZIP, or Office document is password-protected, the password itself isn't stored directly — instead, a **hash** (a scrambled representation of the password) is stored. To recover the password, the hash must first be extracted from the file, then run through a cracking tool that tests candidate passwords until one produces a matching hash.

Both labs below use this same core process (extract hash → crack hash → open file), but with different tools.

---

## Task 1 — Password Cracking with John the Ripper (JTR)

**Goal:** Crack the password of `My Locked PDF1.pdf` using JTR John and JTR Johnny (GUI) on Windows.

**Steps performed:**
1. Downloaded John the Ripper and the Johnny GUI from the official Openwall sources.
2. Installed Johnny and pointed it to the `john.exe` executable.
3. Uploaded the locked PDF to an online PDF hash extractor tool to generate a crackable hash (`$pdf$...` format, using `pdf2john`).
4. Saved the extracted hash into a text file (`hash1.txt`).
5. Opened the hash file in Johnny and started the attack.
6. Johnny successfully cracked the password: **`password1`**
7. Opened the PDF and entered the cracked password to unlock it.

**Screenshots:**
- Johnny GUI with the John the Ripper executable path configured
- Online hash extractor tool showing the extracted `$pdf$...` hash
- Johnny running the attack with the hash loaded
- Johnny showing the cracked password next to the hash
- The unlocked PDF open (final "Congratulations" screen)

---

## Task 2 — Password Cracking with NetworkWalks Tools

**Goal:** Crack the password of the same PDF file using two free browser-based tools built by NetworkWalks — the **Hash Calculator** and the **Password Cracker** — instead of installing JTR locally.

**Steps performed:**
1. Downloaded the same encrypted PDF (`My Locked PDF1.pdf`).
2. Opened the NetworkWalks Hash Calculator and uploaded the PDF, which extracted a crackable `$pdf$...` hash directly in the browser (computed locally, no upload to a server).
3. Copied the full hash value.
4. Opened the NetworkWalks Password Cracker, pasted the hash, and ran a dictionary attack using the built-in wordlist.
5. The tool matched the password after trying several candidates: **`password1`**
6. Opened the PDF and entered the password to confirm it unlocked successfully.

**Screenshots:**
- Hash Calculator with the PDF uploaded and hash displayed
- Password Cracker with the hash pasted in, before starting
- Password Cracker mid-attack (list of attempted passwords)
- "Password Cracked Successfully" result screen
- The unlocked PDF open (final "Congratulations" screen)

---

## Key Takeaways

- Encryption is reversible with the correct key; hashing is one-way — you can't reverse a hash, only guess and check against it.
- Both a locally-installed tool (JTR/Johnny) and browser-based tools (NetworkWalks Hash Calculator / Password Cracker) extract and crack a PDF password hash using the same underlying method (`pdf2john`/`pdf2hashcat` format).
- The cracked password (`password1`) is simple and common — this is exactly why weak/dictionary-based passwords are cracked quickly, while longer, mixed-character passwords resist dictionary attacks far better.

## Tools Used
- [John the Ripper](https://www.openwall.com/john/)
- [Johnny (JTR GUI)](https://openwall.info/wiki/john/johnny)
- [NetworkWalks Hash Calculator](https://networkwalks.com/hash-calculator/)
- [NetworkWalks Password Cracker](https://networkwalks.com/password-cracker/)
- [Online Hash Crack — PDF Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php)
