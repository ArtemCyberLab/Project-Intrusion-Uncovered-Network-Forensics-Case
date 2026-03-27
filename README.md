🎯 Project Goal

In this project, Project-Intrusion-Uncovered-Network-Forensics-Case, my goal was to analyze a captured network traffic file (PCAP) to investigate a real-world intrusion. I needed to identify how the attacker gained access to the system, understand the techniques used during the attack, and reconstruct the full attack chain step by step.

Additionally, I focused on extracting hidden data from the traffic, including credentials, malicious files, and encrypted communication. The final objective was to uncover the attacker’s actions and recover all flags hidden inside the captured data.

📝 Project Description

In this project, I worked with a PCAP file that contained network traffic from a compromised environment. I started my analysis using Wireshark to understand the structure of the traffic and identify the protocols involved.

During the investigation, I discovered that email protocols such as SMTP, POP3, and IMAP were used without encryption. This allowed me to capture login credentials in plaintext. By following TCP streams, I identified valid user credentials.

Next, I analyzed email traffic and found a suspicious message containing an attachment encoded in base64. After decoding it using CyberChef, I obtained an ODS (OpenDocument Spreadsheet) file. By extracting its contents, I discovered a malicious macro that downloads and executes a file from a remote server.

I then analyzed HTTP traffic and successfully extracted the malicious executable (client.exe), even though it was not clearly identified by Wireshark. After that, I performed reverse engineering using Ghidra to analyze the binary.

During this step, I identified how the malware generated an AES encryption key. This key was later used to decrypt suspicious TLS-like traffic found in the PCAP. The communication did not follow a normal TLS handshake, which suggested the use of custom encryption.

By applying the extracted AES key and using AES-CBC decryption, I was able to recover hidden data from the encrypted traffic, including additional flags.

✅ Conclusion

This project showed how attackers can exploit insecure configurations, such as unencrypted communication protocols, to gain access to sensitive information.

I gained hands-on experience in network forensics, including traffic analysis, credential extraction, and detection of malicious activity in email communications. I also improved my skills in working with encoded data, extracting files, and reverse engineering malware.

One of the most important lessons from this project was understanding the full attack chain — from initial access to execution and encrypted communication.

Overall, this project strengthened my practical skills as a security analyst and improved my ability to investigate real-world cyber incidents.
