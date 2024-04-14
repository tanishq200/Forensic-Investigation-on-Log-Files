# Forensic Investigation on Log Files

## Overview

This document outlines the forensic analysis conducted on the log files and related data from a cyber attack on ENPM685 Waffle Co., a tech startup that experienced unauthorized access during the development of their new web-based ordering feature. The investigation aimed to understand how the attack was carried out, identify what the attacker did, and determine the extent of the data accessed.

## Tools Used

- **Wireshark**: Used to analyze network packets and reconstruct the sequence of events.
- **Splunk**: Employed for aggregating and analyzing the log data.
- **tcpdump**: Used to capture the network traffic during the attack, helping in identifying malicious activities.

## Files Analyzed

- **web.tar**: Contains the web directory files written in PHP, reflecting the website’s structure and codebase.
- **julia-home.tar**: Contains the contents of Julia’s home directory.
- **logs.tar**: Includes all logs stored in /var/log, providing crucial information on system activities during the attack.
- **final.pcap**: A tcpdump capture file that potentially contains the attacker’s traffic.

## Analysis Summary

### Attack Details

- **Initial Access**: The attacker exploited a file upload vulnerability on the Waffle Co. website, which allowed uploading of any file type. This enabled the attacker to upload a malicious PHP file, gaining remote execution capabilities.
- **Exploitation**: Using the malicious PHP file named "pwn3d.php," the attacker executed commands remotely, leading to a directory traversal attack and eventually obtaining administrative access.
- **Data Breach**: The attacker changed Julia's password, gained SSH access, and extracted sensitive data including email addresses, phone numbers, and proprietary recipes.

### Key Findings

- **Vulnerability Exploited**: The website allowed unrestricted file uploads, which the attacker used to upload a malicious PHP script.
- **Attack Execution**: The attacker uploaded a benign image file to probe the system before uploading the malicious PHP file.
- **Data Accessed**: Sensitive data was accessed and extracted, including customer and order data, as well as proprietary recipes.

## Recommendations

- **Security Enhancements**: Implement strict file type validation for uploads, apply robust input sanitization, and restrict executable file permissions.
- **Monitoring and Response**: Enhance monitoring of network traffic and logs. Establish protocols for immediate response to detected anomalies.
- **Forensic Readiness**: Maintain regular backups of critical data and ensure that logging mechanisms are capable of capturing detailed information on potential attacks.

## Challenges Faced

- **Decoding Obfuscated Code**: The attacker used complex obfuscation techniques to hide the malicious payload, making detection and analysis challenging.
- **Persistent Access and Data Exfiltration**: The attacker was able to maintain access long enough to extract significant amounts of sensitive data.

## Conclusion

This investigation has highlighted critical vulnerabilities in the startup’s web application and provided insights into the attacker’s methods and objectives. It underscores the importance of rigorous security practices in the development and deployment of web applications, especially when handling sensitive data.
