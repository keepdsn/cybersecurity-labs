
# 🛡️ CyberDefenders - Amadey

- **Difficulty:** Easy  
- **Category:** Endpoint Forensics
- **Platform:** [CyberDefenders](https://cyberdefenders.org/dashboard/)
- **Tactics:**  `Execution`, `Persistence`, `Privilege Escalation`, `Defense Evasion`, `Command and Control`, `Exfiltration`
  
---

## 📌 Scenario

An after-hours alert from the Endpoint Detection and Response (EDR) system flags suspicious activity on a Windows workstation. The flagged malware aligns with the Amadey Trojan Stealer. Your job is to analyze the presented memory dump and create a detailed report for actions taken by the malware.

![Cyberdefenders screenshot](./amad_screen.jpg)

---

## 🔍 Step-by-Step

### 1️⃣ In the memory dump analysis, determining the root of the malicious activity is essential for comprehending the extent of the intrusion. What is the name of the parent process that triggered this malicious behavior?

> After confirming from external threat intelligence sources that the malware in question was Amadey, I reviewed known indicators such as process names and behaviors associated with it. Then, using Volatility’s `pslist` and `pstree`, I examined the process hierarchy and identified a suspicious executable. Correlating its execution time and behavior with typical Amadey traits allowed me to determine its parent process — revealing how the initial compromise began under a seemingly legitimate context.

### 2️⃣ Once the rogue process is identified, its exact location on the device can reveal more about its nature and source. Where is this process housed on the workstation?

> Leveraged `cmdline` to extract the complete execution path of the malware process. The retrieved path revealed if the executable was running from a suspicious directory typically used by droppers.

### 3️⃣ Persistent external communications suggest the malware's attempts to reach out C2C server. Can you identify the Command and Control (C2C) server IP that the process interacts with?

> Ran `netscan` to analyze open and closed network connections. Matching the malware’s PID to external IP addresses helped confirm communication.

### 4️⃣ Following the malware link with the C2C, the malware is likely fetching additional tools or modules. How many distinct files is it trying to bring onto the compromised workstation?

> I used Volatility’s `dump` to extract memory based on `PID`. I then parsed the dumped memory using strings combined with `grep "GET"` to isolate outbound HTTP requests. By counting the number of unique `GET` requests, I estimated how many distinct payloads the malware attempted to fetch from its Command and Control server during the infection lifecycle.

### 5️⃣ Identifying the storage points of these additional components is critical for containment and cleanup. What is the full path of the file downloaded and used by the malware in its malicious activity?

> Cross-referenced file names from previous steps with `filescan` to uncover full paths. 

### 6️⃣ Once retrieved, the malware aims to activate its additional components. Which child process is initiated by the malware to execute these files?

> Inspected `pstree` to determine which child processes the malware created.

### 7️⃣ Understanding the full range of Amadey's persistence mechanisms can help in an effective mitigation. Apart from the locations already spotlighted, where else might the malware be ensuring its consistent presence?

> Again,used `filescan` to enumerate file paths present in memory. Among the discovered entries, one pointed to the Windows Task Scheduler directory, indicating that a scheduled task had likely been created for persistence. This revealed that Amadey maintained access through task-based execution triggered during system activity.

---

## 🛠 Tools & Techniques Used

- Volatility 3:
  - `pslist`, `pstree` — for analyzing process hierarchy and identifying parent-child relationships 
  - `cmdline` — for extracting full execution paths of running processes 
  - `netscan` — for detecting external network communications and C2 activity
  - `filescan` — for identifying file references in memory, including scheduled tasks
  - `procdump` — for extracting memory of specific processes for further analysis
  - `strings` + `grep` — for locating HTTP GET requests and other indicators in memory`
- Manual review of extracted paths and process behavior based on known Amadey traits

---

## 🧠 Notes

- Identified malicious execution and payload delivery by focusing on Amadey's typical behaviors
- Confirmed network activity and file retrieval via memory-based string analysis
- Observed persistence through scheduled task creation revealed in memory structure
- This challenge reinforced my skills in:
  - Process chain reconstruction via memory
  - Analyzing malware communications and file downloads
  - Tracing persistence mechanisms from memory artifacts

---

## 📂 Files

- This challenge included a `.vmem` file.
- No additional attachments.

---

## 🧑‍💻 Author

**Anton Ivanov**  
Cybersecurity Learner | SOC Analyst in progress  
📍 Paradise, NL, Canada  
📫 [keepdsn@icloud.com](mailto:keepdsn@icloud.com)  
🔗 [linkedin.com/in/davniyson](https://linkedin.com/in/davniyson)
