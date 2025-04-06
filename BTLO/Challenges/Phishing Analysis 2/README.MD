# 🛡️ BTLO - Phishing Analysis 2

- **Difficulty:** Easy  
- **Category:** Security Operations
- **Platform:** [Blue Team Labs Online (BTLO)](https://blueteamlabs.online/)  
- **Focus:** TextEditor, Thunderbird
---

## 📌 Scenario

Put your phishing analysis skils to the test by triaging and collecting information about a recent phishing campaign.
A suspicious .eml email file was submitted for analysis. Your task is to examine it and extract critical information related to a potential phishing attempt.

---

## 🔍 Step-by-Step

### 1️⃣ What is the sending email address?:

> Found using the EML Analyzer and verified with the `cat` command.
> - Method: Located in the `From:` header.

### 2️⃣ What is the recipient email address?

> Found using the EML Analyzer and confirmed via `cat`.
> - Method: Located in the `To:` header.

### 3️⃣ What is the subject line of the email?

> Identified using the EML Analyzer and `cat`.
> - Method: Found in the `Subject:` header.

### 4️⃣ What company is the attacker trying to imitate?

> Determined from branding in the message content using the EML Analyzer and verified with `cat`.
> - Method: The spoofed company is visible in the email body.

### 5️⃣ What is the date and time the email was sent?

> Extracted using the following terminal command: `cat email.eml | grep -i date`
> - Note: The date format shown in the EML Analyzer did not match the required format, so it was retrieved directly from the raw `.eml` file.

### 6️⃣ What is the URL of the main call-to-action button?

> Identified using the EML Analyzer and `cat`.
> - Method: Found in the `Subject:` header.
---

## 🧠 Notes

- MITRE ATT&CK is super useful when you break down the scenario by **tactic first**, then narrow it down by technique.
- Not every software in ATT&CK has a clear description — sometimes better to search by **behavior or tactic**, not just names.
- Always check the **Detection** section — it often has real-world event IDs, log types, or tools to monitor.
- Good tools/resources used:
  - 🔍 [MITRE ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/)
  - 🧭 Google with `site:attack.mitre.org` filter
  - 🧰 OSINT & log analysis skills help in threat intelligence

---

## 📂 Files

This challenge has no files attached. Only ATT&CK framework usage and reasoning.

---

## 🖼 Certificate

![BTLO ATT&CK certificate](./attackcert.jpg)



## 🧑‍💻 Author

**Anton Ivanov**  
Cybersecurity Learner | SOC Analyst in progress  
📍 Paradise, NL, Canada  
📫 [keepdsn@icloud.com](mailto:keepdsn@icloud.com)  
🔗 [linkedin.com/in/davniyson](https://linkedin.com/in/davniyson)
