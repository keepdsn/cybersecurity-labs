# 🛡️ BTLO - Phishing Analysis 2

- **Difficulty:** Easy  
- **Category:** Security Operations 
- **Platform:** [Blue Team Labs Online (BTLO)](https://blueteamlabs.online/)  
- **Focus:** TextEditor, Thunderbird

---

## 📌 Scenario

Put your phishing analysis skils to the test by triaging and collecting information about a recent phishing campaign.

# 🛡️ BTLO - EML Phishing Email Analysis

- **Difficulty:** Easy  
- **Category:** Email Analysis  
- **Platform:** [Blue Team Labs Online (BTLO)](https://blueteamlabs.online/)  
- **Focus:** Phishing Email, EML Forensics

---

## 📌 Scenario

A suspicious `.eml` email file was submitted for analysis. Your task is to examine it and extract critical information related to a potential phishing attempt.

---

🔍 Step-by-Step – Questions & Answers

🔹 1. What is the sending email address?

Answer:Found using the EML Analyzer and verified with the cat command.Method: Located in the From: header.

🔹 2. What is the recipient email address?

Answer:Found using the EML Analyzer and confirmed via cat.Method: Located in the To: header.

🔹 3. What is the subject line of the email?

Answer:Identified using the EML Analyzer and cat.Method: Found in the Subject: header.

🔹 4. What company is the attacker trying to imitate?

Answer:Determined from branding in the message content using the EML Analyzer and verified with cat.Method: The spoofed company is visible in the email body.

🔹 5. What is the date and time the email was sent?

Answer:Extracted using the following terminal command:

cat email.eml | grep -i date

Note: The date format shown in the EML Analyzer did not match the required format, so it was retrieved directly from the raw .eml file.

🔹 6. What is the URL of the main call-to-action button?

Answer:Opened the .eml file in a detached virtual machine and manually extracted the link.Reason: The link was embedded in an encoded HTML section and not visible via cat.

🔹 7. What is the first sentence (heading) displayed on the target website (via URL2PNG)?

Answer:URL2PNG was not functional.The link was opened in an isolated virtual machine, and the heading was copied manually from the rendered webpage.

🔹 8. What encoding scheme is used in the email body?

Answer:A very common encoding scheme was used — Base64.Method: Located in the email headers as:

Content-Transfer-Encoding: base64

🔹 9. What is the URL used to retrieve the company’s logo in the email?

Answer:Found using the EML Analyzer.Reason: The image source was located in the HTML body, which was Base64-encoded, and not visible using cat or grep.

🔹 10. What is the Facebook username found in one of the URLs?

Answer:Extracted using the EML Analyzer.Reason: The URL containing the Facebook profile was found inside an encoded HTML section, inaccessible via cat.

🛠 Tools & Techniques Used

cat, grep — for inspecting plaintext header

EML Analyzer — for decoding Base64 and viewing HTML body

Isolated Virtual Machine — for safely opening potentially malicious links

Manual inspection of raw EML file with a text editor

🧠 Notes

Many phishing emails use Base64 to encode HTML content and obfuscate malicious links or embedded resources.

Always analyze emails in a sandbox or isolated VM to avoid accidental execution of malicious content.

Email headers often reveal key metadata without needing to decode the body.

This challenge improved my skills in:

Email header analysis

Recognizing encoding schemes

Using safe environments for dynamic inspection

📂 Files

This challenge included a .eml file containing a Base64-encoded HTML phishing email.

No additional attachments.



## 🖼 Certificate

![BTLO Certificate](./btlo_eml_certificate.jpg)

---

## 👤 Author

**Anton Ivanov**  
Cybersecurity Learner | SOC Analyst (in progress)  
📍 Paradise, NL, Canada  
📩 [keepdsn@icloud.com](mailto:keepdsn@icloud.com)  
🔗 [linkedin.com/in/davniyson](https://linkedin.com/in/davniyson)

---

## 🔍 Step-by-Step

### 1️⃣ Question:

> What is the sending email address?

**🛠 How I solved it:**

- Found using the EML Analyzer and verified with the cat command.
Method: Located in the From: header.

### 2️⃣ Question:

> You were analyzing a log and found uncommon data flow on port 4050. What APT group might this be?

**🛠 How I solved it:**

- I searched Google for information about activity on TCP port 4050
- Identified a known association between this port and a specific tool or malware
- Cross-checked the results against the MITRE ATT&CK database
- Found the APT group documented by MITRE as using this port

### 3️⃣ Question:

> The framework has a list of 9 techniques that falls under the tactic to try to get into your network. What is the tactic ID?

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
