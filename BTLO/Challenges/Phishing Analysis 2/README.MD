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

> ### Answer:
> Found using the EML Analyzer and verified with the `cat` command.
> - Method: Located in the `From:` header.

### 2️⃣ What is the recipient email address?

> ### Answer:
> Found using the EML Analyzer and confirmed via `cat`.
> Method: Located in the `To:` header.

### 3️⃣ What is the subject line of the email?

> ### Answer:
> Identified using the EML Analyzer and `cat`.
> Method: Found in the `Subject:` header.

**🛠 How I solved it:**

- Opened the MITRE ATT&CK site → went to the Tactics section. 
- Looked for the one responsible for getting into the network.
- Found Initial Access — it had exactly 9 techniques. Took the ID from there.

### 4️⃣ Question:

> A software prohibits users from accessing their account by deleting, locking the user account, changing password etc.
> What such software has been documented by the framework?

**🛠 How I solved it:**

- At first I tried searching in the Software section, but didn’t find anything that matched the description.
- Then I checked the Impact tactic — since it’s about locking users out. 
- There I found the right software, even though its main description in the Software section focuses on something else.

### 5️⃣ Question:

> Using ‘Pass the Hash’ technique to enter and control remote systems on a network is common.
> How would you detect it in your company? 

**🛠 How I solved it:**

- I searched for Pass the Hash in the MITRE ATT&CK framework and found it.
- Then I went to the Detection section of that technique and found the answer.
  
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
