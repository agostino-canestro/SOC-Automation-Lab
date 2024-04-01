<h1>SOC Automation Suite</h1>

<h2>Description</h2>
The SOC Automation Suite aims to establish a proficient and effective security monitoring and incident response framework, utilizing tools such as Wazuh, TheHive, shuffler.io, and VirusTotal. Wazuh serves as the core security monitoring and intrusion detection system, while TheHive acts as the central platform for incident response and case management. Shuffler.io facilitates workflow automation and integrates various security tools to expedite the response process. VirusTotal contributes threat intelligence and malware analysis capabilities. Additionally, the lab leverages DigitalOcean to secure a public IP address for TheHive and Wazuh and to implement a firewall, further enhancing the security infrastructure and ensuring controlled access. The lab also utilizes Oracle VM VirtualBox to provision a virtual machine, providing a flexible and isolated environment for the setup and operation of the lab. Collectively, these components minimize manual labor and accelerate the response to potential threats.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Wazuh</b>
- <b>TheHive</b>
- <b>Shuffler.io</b>
- <b>VirusTotal</b>
- <b>DigitalOcean</b>
- <b>OracleVM VirtualBox</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> 

<h2>Project Walk-through:</h2>

<p align="center">
Step 1: Build a visual representation to map out the lab and how the different components will interact with one another: <br/>
<img src="https://i.imgur.com/EuzZ9Lc.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 2: Use Oracle VM VirtualBox to provision a Windows 10 virtual machine:  <br/>
<img src="https://i.imgur.com/2vbGhZn.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 3: Download and install Symon. This is used for enhancing visibility into system activities, aiding in threat detection by providing detailed logs for monitoring suspicious behavior. Its integration with other tools like Wazuh and TheHive in the SOC Automation Lab allows for a comprehensive and automated response to security events, thereby strengthening the overall security monitoring and incident response framework: <br/>
<img src="https://i.imgur.com/mnIXbQs.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 4: Use DigitalOcean to create a Droplet named Wazuh. A Droplet is a virtual private server that allows you to obtain a public IP address, which then allows us to access Wazuh over the internet:  <br/>
<img src="https://i.imgur.com/u7eqy1a.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/kFRVVWZ.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 5: Create a Firewall to protect your virtual private server:  <br/>
<img src="https://i.imgur.com/U6hLIzX.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/TxY3trj.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 6: Use SSH to connect to the Wazuh server to perform any updates and download Wazuh. The login information displayed at the end of installation will allow you to login to the Wazuh dashboard:  <br/>
<img src="https://i.imgur.com/JwrqLUK.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/PsQyb16.png)" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/Lnpp5SS.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 7: Use DigitalOcean to create another droplet for TheHive. This allows us to be able to connect to TheHive via the internet using the Public IP Address that the droplet provides:  <br/>
<img src="https://i.imgur.com/CVhvZ7O.png height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 8: Add TheHive droplet to the same firewall that you added the Wazuh droplet too:  <br/>
<img src="https://i.imgur.com/XX8oWtp.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 9: Use SSH to connect to the TheHive server to perform any updates and download TheHive along with its components.:  <br/>
<img src="https://i.imgur.com/SJRdMOW.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 10: Download and configure Wazuh and TheHive along with their components:  <br/>
<img src="https://i.imgur.com/59Hl1Gz.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/JhdVyPm.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/1cPkeld.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/UEd6DAs.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/3aQhuFI.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/cSBrdht.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 11: Download Mimikatz and add an exclusion within Windows Security to allow the malicious script to be able to run without being stopped. Using Powershell, run the script:  <br/>
<img src="https://i.imgur.com/y9nCtEx.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/kI5Docf.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 12: Navigate to the Wazuh Dashboard to see the Mimikatz activity being logged:  <br/>
<img src="https://i.imgur.com/7bggJ7p.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/e8PVNW0.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/l871tir.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/Nr2aS2Q.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />
Step 13: Use shuffler.io to connect the different security tools together and automate workflows, with the last step being sending an email alert.
<p align="center">
  1. Wazuh alerts -> SHA256 regex: When Wazuh generates an alert, it often contains various pieces of information about the security incident, including file hashes. The SHA256 regex connection is used to extract the SHA256 hash value from the Wazuh alert using a regular expression (regex). This hash value is typically associated with a suspicious file or malware sample. <br>
  2. SHA256 regex -> VirusTotal: Once the SHA256 hash is extracted, it is sent to VirusTotal for analysis. VirusTotal checks the hash against its database of known malware and provides a report on the file's reputation, any detected malware signatures, and other relevant threat intelligence. This information helps to determine whether the file associated with the alert is malicious.<br>
  3. VirusTotal -> TheHive: If VirusTotal identifies the file as malicious, the information from the VirusTotal report is forwarded to TheHive. In TheHive, a new case or alert is created (or an existing one is updated) with the details from the VirusTotal report. This allows security analysts to investigate the incident further, collaborate on the response, and document their findings and actions. <br>
  4. VirusTotal -> Email: In addition to sending the information to TheHive, the workflow can also be configured to send an email notification if VirusTotal identifies the file as malicious. This email can alert security personnel or other stakeholders about the potential threat, providing them with immediate information about the incident and enabling a quicker response:
</p>
<p align="center">
<img src="https://i.imgur.com/ljvgA7K.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/TM3e2ly.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<img src="https://i.imgur.com/WV8HUXQ.png" height="80%" width="80%" alt="SOC Automation Lab Steps"/>
<br />
<br />



