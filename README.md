# Bug Hunting and Dorking Techniques

This README file provides a structured guide on how to use **dorking techniques** with tools like **Shodan, GitHub, Firebase, and Bitbucket** for **ethical reconnaissance** in **bug hunting**. It includes practical payloads, testing methods, and best practices to identify potential security risks in web applications.

> **Disclaimer**: Ethical hacking must be conducted only with explicit authorization from the target, such as through a **Bug Bounty Program**. Unauthorized access or exploitation of systems is **illegal**.

---

## Table of Contents

1. [Shodan Dorking (Internet-Exposed Assets)](#shodan-dorking-internet-exposed-assets)
2. [GitHub Dorking (Leaked Code & Secrets)](#github-dorking-leaked-code--secrets)
3. [Firebase Dorking (Exposed Databases)](#firebase-dorking-exposed-databases)
4. [Bitbucket Dorking (Source Code & Credentials)](#bitbucket-dorking-source-code--credentials)
5. [Potential Findings](#potential-findings)
6. [Ethical Hacking Guidelines](#ethical-hacking-guidelines)
7. [Bug Bounty Programs](#bug-bounty-programs)

---

## Shodan Dorking (Internet-Exposed Assets)

Shodan is a search engine that indexes devices and services exposed to the internet. It is widely used for reconnaissance to identify open ports, databases, and misconfigured systems.
#### Common Shodan Queries:

- **Open Databases**:
  ```plaintext
  product:"MongoDB" host:facebook.com
  product:"Elasticsearch" host:facebook.com
  product:"PostgreSQL" host:facebook.com
  ```

- **Exposed Industrial Control Systems (ICS)**:
  ```plaintext
  port:502 host:facebook.com
  port:47808 host:facebook.com
  ```

- **Security Cameras & IoT Devices**:
  ```plaintext
  hostname:facebook.com port:554 has_screenshot:true
  ```

- **Default Credentials**:
  ```plaintext
  default password host:facebook.com
  ```

- **Vulnerable VPNs & RDP**:
  ```plaintext
  port:3389 host:facebook.com
  port:500 host:facebook.com
  ```

- **Misconfigured Cloud Storage (e.g., AWS S3 Buckets)**:
  ```plaintext
  title:"index of /" bucket host:facebook.com
  ```

- **Unpatched Systems**:
  ```plaintext
  vuln:CVE-2023-* host:facebook.com
  ```

### Recommended Testing Steps:
1. Perform Shodan searches using relevant dorks.
2. Check for exposed services and assess potential misconfigurations.
3. Identify publicly available login pages and check for default credentials.

---

## GitHub Dorking (Leaked Code & Secrets)

GitHub often contains accidentally exposed credentials, API keys, and configuration files.

#### Common GitHub Queries:

- **API Keys & Tokens**:
  ```plaintext
  filename:.env "API_KEY=" site:github.com
  filename:config.json "password" site:github.com
  ```

- **AWS Credentials**:
  ```plaintext
  AWS_SECRET_ACCESS_KEY filetype:txt site:github.com
  ```

- **Private SSH Keys**:
  ```plaintext
  filename:id_rsa site:github.com
  ```

- **Database Credentials**:
  ```plaintext
  DB_PASSWORD filetype:env site:github.com
  ```

- **Email Passwords in Code**:
  ```plaintext
  smtp password filetype:php site:github.com
  ```

- **Slack & Discord Tokens**:
  ```plaintext
  "xoxb-" site:github.com
  ```

### Recommended Testing Steps:
1. Use GitHub’s search feature or Google Dorks to find exposed credentials.
2. Clone repositories containing sensitive data and verify their authenticity.
3. Report findings responsibly to the affected organization.

---

## Firebase Dorking (Exposed Databases)

Firebase is widely used for mobile and web applications. Sometimes, misconfigurations expose databases to unauthorized access.

#### Common Firebase Queries:

- **Find Open Firebase Instances**:
  ```plaintext
  site:firebaseio.com
  ```

- **Check if Read/Write Permissions are Open**:
  ```plaintext
  intitle:"Index of /" site:firebaseio.com
  ```

- **Leaked User Data**:
  ```plaintext
  intext:"users" site:firebaseio.com
  ````

### Recommended Testing Steps:
1. Search for open Firebase databases using Google Dorks.
2. Attempt to retrieve data without authentication.
3. Check if unauthorized modifications are possible.

---

## Bitbucket Dorking (Source Code & Credentials)

Bitbucket, similar to GitHub, hosts repositories that may contain sensitive information.

#### Common Bitbucket Queries:

- **Public Repos with API Keys**:
  ```plaintext
  site:bitbucket.org "API_KEY="
  ```

- **Open Config Files**:
  ```plaintext
  site:bitbucket.org "db_password"
  ```

- **Leaked CI/CD Secrets**:
  ```plaintext
  filename:.gitlab-ci.yml site:bitbucket.org
  ```

- **Misconfigured Private Keys (SSH)**:
  ```plaintext
  filename:id_rsa -extension:pub site:bitbucket.org
  ```

### Recommended Testing Steps:
1. Search for repositories containing sensitive configuration files.
2. Extract useful information and assess potential security risks.
3. Notify affected repository owners responsibly.

---

## Potential Findings

By applying these techniques, you may discover:

- **Misconfigured Databases**: Firebase and cloud databases with open permissions.
- **Leaked API Keys**: Credentials for AWS, Slack, Discord, and more.
- **Exposed Services**: Identifying open ports and services that shouldn't be public.
- **Publicly Accessible Code**: Sensitive files and configurations unintentionally exposed in repositories.

---

## Ethical Hacking Guidelines

> Always follow these principles when conducting ethical hacking and bug bounty research:

1. **Get Permission**: Only test systems where you have explicit authorization.
2. **Follow Legal Boundaries**: Ensure compliance with relevant laws.
3. **Report Vulnerabilities Responsibly**: Use proper channels to notify affected organizations.

---

## Bug Bounty Programs

If you discover a vulnerability, consider submitting it to the relevant **Bug Bounty Program** for recognition and rewards.

- **[Facebook Bug Bounty Program](https://www.facebook.com/whitehat)**
- **[Google Vulnerability Reward Program](https://bughunters.google.com/)**
- **[HackerOne](https://www.hackerone.com/) & [Bugcrowd](https://www.bugcrowd.com/)**

---

## Conclusion

This guide provides a structured approach to **ethical reconnaissance** using **Shodan, GitHub, Firebase, and Bitbucket**. By applying these dorking techniques, you can identify misconfigurations, exposed credentials, and security risks in web applications.

Always ensure your activities are **ethical and legal**, follow responsible disclosure practices, and contribute to a safer internet.
