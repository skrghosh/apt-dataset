# Caldera APT Simulation Datasets

This repository contains datasets from a series of APT (Advanced Persistent Threat) simulations conducted using [Caldera](https://caldera.mitre.org/), guided by the best practices from MITRE's [Center for Threat-Informed Defense](https://github.com/center-for-threat-informed-defense/adversary_emulation_library). The simulations represent a variety of attack scenarios, providing a rich resource for understanding the nature of sophisticated cyber threats.

## Dataset Overview

The datasets encompass multiple attack scenarios simulated in a controlled environment. Each scenario's dataset includes comprehensive logs with details of benign and malicious activities, offering invaluable insights for cybersecurity analysis.

### Campaign Details

| Campaign Name | Duration      | Attack Vector       | Records (#) | Benign (%) |
|---------------|---------------|---------------------|-------------|------------|
| APT 29        | 18h 55m       | Multiple(CALDERA)   | 3.74M       | 99.37%     |
| FIN6          | 11h 05m       | Multiple(CALDERA)   | 2.35M       | 99.69%     |
| menuPass      | 14h 35m       | Multiple(CALDERA)   | 6.34M       | 99.83%     |
| Wizard Spider | 24h 09m       | Multiple(CALDERA)   | 3.69M       | 99.78%     |
| OilRig        | 13h 16m       | Multiple(CALDERA)   | 6.19M       | 99.97%     |

<!--| Redline       | 3h 50m        | File Execution      | 2.01M       | 99.51%     |
| Remcos        | 1h 44m        | File Execution      | 660K        | 97.47%     |
| Agent Tesla   | 6h 03m        | File Execution      | 2.69M       | 99.98%     |
| AsyncRAT      | 6h 45m        | File Execution      | 1.37M       | 99.93%     |
| Amadey        | 5h 16m        | File Execution      | 5.19M       | 99.68%     |-->


These datasets were generated by emulating various attack vectors as outlined by MITRE, primarily involving the CALDERA automation framework, as well as general file execution techniques. They offer an array of records ranging from hundreds of thousands to several million, with the overwhelming majority representing benign activities to provide realistic baseline behavior.

## Dataset Details

- **Total Records:** See the table above for the record count of each campaign.
- **Target System:** Windows 10 (64-bit).
- **Duration of Simulation:** Times vary per simulation campaign as detailed above.
- **Benign Records:** To mimic real-world environments where these attacks are generally executed, we created this dataset to contain a majority of benign daily activities of users with a minuscule amount of malicious activities, as outlined by MITRE. These benign activities include surfing the web by visiting several random websites, downloading different types of files from websites, uploading different files to websites, opening system files, creating different file types, editing (and renaming) and saving those updated files, deleting different files, running several user commands from PowerShell or cmd, running different applications, creating, renaming, deleting several directories, copying files and folders, compressing and decompressing files, etc. More than 99% of the data for each scenario represents benign data, as shown above.
- **Data Model:** The audit logs are modeled based on MITRE's CAR (Cyber Analytics Repository) and FiveDirections' eCAR data model. More details about the data model can be found [here](https://github.com/FiveDirections/OpTC-data/blob/master/ecar.md).


## Ground Truth

Corresponding ground truths for each scenario are included in the Ground Truth directory to facilitate validation and benchmarking efforts.


## FIN6 Campaign Tactics and Techniques

| Tactics            | Techniques                                       | Abilities                                  |
|--------------------|--------------------------------------------------|--------------------------------------------|
| Collection         | T1560.001: Archive Collected Data: Archive via Utility |  Compress Files with 7zip (7z.exe) |
| Credential-access  | T1003.001: OS Credential Dumping: LSASS Memory - Invoke-Mimikatz |  PowerSploit Invoke-Mimikatz |
|                    | T1003.001: OS Credential Dumping: LSASS Memory - Windows Credential Editor (WCE) |  WCE Credential Access      |
| Discovery          | T1087.002: Account Discovery: Domain Account    |  Enumerate AD person objects |
|                    | T1018: Remote System Discovery                  |  Enumerate AD computer objects |
|                    | T1482: Domain Trust Discovery                   |  Enumerate AD Organizational Units |
|                    | T1016: System Network Configuration Discovery   |  Enumerate AD trust objects |
|                    | T1069.002: Permission Groups Discovery: Domain Groups Units |  Enumerate AD subnets, Enumerate AD groups |
| Execution          | T1569.002: System Services: Service Execution   |  PsExec Remote Command |
|                    | T1047: Windows Management Instrumentation       |  WMIC Remote Process Execution |
| Exfiltration       | T1041.005: Exfiltration Over C2 Channel         |  Exfil staged directory |
| Privilege-escalation | T1134: Access Token Manipulation              |  PowerSploit Named-Pipe Impersonation |


## menuPass Campaign Tactics and Techniques

| Tactics             | Techniques                                       | Abilities                             |
|---------------------|--------------------------------------------------|---------------------------------------|
| Collection          | T1560.001: Archive Collected Data: Archive via Utility | Archive Collected Data - Archive via Utility |
|                     | T1074.001: Local Data Staging                    |  Recycle Bin Staging    |
| Discovery           |                                                  |  ProgramData-Temp-Creation |
|                     | T1105: Ingress Tool Transfer                     |  Ingress Tool Transfer  |
|                     | T1135: Network Share Discovery                   |  Network Share Discovery |
|                     | T1018: Remote System Discovery                   |  Remote System Discovery |
|                     | T1046: Network Service Scanning                  |  Network Service Scanning |
|                     | T1016: System Network Configuration Discovery    |  System Network Configuration Discovery |
| Execution           | T1047: Windows Management Instrumentation        |  Windows Management Instrumentation |
| Exfiltration        | T1537: Transfer Data to Cloud Account            |  Transfer Data to Cloud Account |
| Lateral-movement    | T1569.002: System Services: Service Execution    |  Service Execution |


## Wizard Spider Campaign Tactics and Techniques

| Tactics            | Techniques                                        | Abilities                                                               |
|--------------------|---------------------------------------------------|-------------------------------------------------------------------------|
| Collection         | T1114.001: Email Collection: Local Email Collection | Emotet Scrape Email Addresses from Outlook   |
| Command-and-Control | T1105: Ingress Tool Transfer                       |  Emotet Download Outlook Scraper DLL          |
|                    | T1486: Data Encrypted for Impact                   | Wizard Spider Downloads kill.bat, Wizard Spider Downloads window.bat,   |
|                    |                                                   | Wizard Spider Downloads ryuk.exe, Wizard Spider Executes Ryuk Ransomware|
| Credential-Access  | T1552: Unsecured Credentials                       |  Emotet Scrape Email Content From Outlook     |
|                    | T1558.003: Steal or Forge Kerberos Tickets:        | TrickBot Perform Kerberoasting                                          |
|                    | Kerberoasting                                      | Wizard Spider Create Volume Shadow Copy                                 |
|                    | T1003.003: OS Credential Dumping: NTDS            | Wizard Spider Save Registry Hive                                        |
|                    | T1003.002: OS Credential Dumping: Security Account | Manager                                                                 |
| Discovery          | T1082: System Information Discovery                |  Emotet System Info Discovery                 |
|                    | T1057: Process Discovery                           | Emotet Process Discovery                                                |
|                    | T1007: System Service Discovery                    | TrickBot System Information Discovery                                   |
|                    | T1087.001: Account Discovery: Local Account        | TrickBot System Information Discovery                                   |
|                    | T1087.002: Account Discovery: Domain Account       | TrickBot System Service Discovery (systeminfo)                          |
|                    | T1016: System Network Configuration Discovery      | TrickBot Local Account Discovery, TrickBot Domain Account Discovery     |
|                    | T1049: System Network Connections Discovery        | TrickBot System Network Configuration Discovery                         |
|                    | T1482: Domain Trust Discovery                      | TrickBot System Network Connections Discovery                           |
|                    | T1069: Permission Groups Discovery                 | TrickBot System Information Discovery (net config)                      |
|                    | T1069.002: Permission Groups Discovery: Domain Groups | TrickBot Domain Trust Discovery, TrickBot Permission Groups Discovery, |
|                    |                                                   | Wizard Spider Domain Group Discovery                                    |
| Exfiltration       | T1041: Exfiltration Over C2 Channel                |  Data from staged file (T1074) and            |
|                    |                                                    | Exfiltration over C2 Channel (T1041)                                    |
| Impact             | T1489: Service Stop                                | Wizard Spider Runs kill.bat  |
|                    | T1490: Inhibit System Recovery                     | Wizard Spider Runs window.bat  |
| Persistence        | T1547.001: Boot or Logon Autostart Execution: Registry Run Keys / Startup Folder                | Emotet Persistence  |
|                    | T1547.004: Boot or Logon Autostart Execution: Winlogon Helper DLL | Wizard Spider Registry Persistence                      |


## OilRig Campaign Tactics and Techniques

| Tactics           | Techniques                                      | Abilities                                   |
|-------------------|-------------------------------------------------|---------------------------------------------|
| Command-and-Control| T1105: Ingress Tool Transfer                    | OilRig Download Plink                       |
|                   | T1572: Protocol Tunneling                       | OilRig Plink                                |
| Credential-access | T1555.004: Credentials from Password Stores:    | OilRig Dump Credentials from                |
|                   | Windows Credential Manager                      | Windows Credential Manager                  |
| Defense-evasion   | T1082: Hide Artifacts: Hidden Files & Directories | OilRig Set file hidden attribute           |
| Discovery         | T1083: System Information Discovery             | OilRig Execute VBS payload to               |
|                   |                                                 | collect hostname                            |
|                   | T1033: System Owner/User Discovery              | OilRig Current User                         |
|                   | T1016: System Network Configuration Discovery   | OilRig Collect hostname                     |
|                   | T1087.002: Account Discovery: Domain Account    | OilRig Network Interface Configuration      |
|                   | T1069.002: Permission Groups Discovery:         | OilRig Domain Account Discovery             |
|                   | Domain Groups                                   | OilRig Group Account Discovery              |
|                   | T1087.001: Account Discovery: Local Account     | OilRig "domain admins" Group Discovery      |
|                   | T1069.001: Permission Groups Discovery:         | OilRig Local Account Discovery              |
|                   | Local Groups                                    | OilRig "administrators" local group discovery|
|                   | T1049: System Network Connections Discovery     | OilRig View Network Connections             |
|                   | T1057: Process Discovery                        | OilRig Process discovery                    |
|                   | T1007: System Service Discovery                 | OilRig System Service Discovery             |
|                   | T1012: Query Registry                           | OilRig System Information Discovery         |
|                   | T1018: Remote System Discovery                  | OilRig Query Registry                       |
|                   |                                                 | OilRig "SQL Admins" Group Discovery         |
|                   |                                                 | OilRig nslookup WATERFALLS                  |
|                   |                                                 | OilRig Execute VBS payload to collect username|
| Exfiltration      | T1041: Exfiltration Over C2 Channel             | OilRig Exfil fsociety.dat                   |

These tables provide a snapshot of the adversarial techniques and corresponding behaviors replicated during the simulation to emulate the different APT group's known tactics and capabilities as outlined by MITRE.



## Usage

These datasets are versatile, suited for:
- **Research:** Understand APT behaviors and patterns.
- **Machine Learning:** Train models to differentiate between benign and malicious actions.
- **Benchmarking:** Evaluate the effectiveness of security systems against simulated APT attacks.

---

**Anonymization Update:**
We are currently in the process of anonymizing the dataset to remove identifiable keywords. This will be completed in the upcoming weeks.

---

## License

This dataset is made available under the Creative Commons Attribution 4.0 International license (CC BY 4.0). You are free to share and adapt this dataset for any purpose, even commercially, as long as you provide appropriate credit, provide a link to the license, and indicate if changes were made.

When citing this dataset, please use the following format:

> [Name of Authors]. Citar: Cyberthreat Intelligence-driven Attack Reconstruction. [Online].

A full copy of the license can be found [here](https://creativecommons.org/licenses/by/4.0/).


## Acknowledgements

Special thanks to MITRE and the Caldera for releasing the tools and guidance in creating these simulations.

---

For any discrepancies found in the datasets or inquiries about their use, please open an issue in this repository. Contributions and suggestions are always appreciated!
