# Part 1: Windows OS Hardening

Security Policies & System Configurations

---

## Task 1: Configure Local Security Policy

![Screenshot](screenshots/windows/task1-local-security-policy.png)

### Configuration Steps
1. Open the Start menu and search for "Local Security Policy" (or type `secpol.msc`).
2. Navigate to the target policy (e.g., Security Settings > Account Policies).
3. Double-click the policy, change the settings, and click "Apply" then "OK".

### Vulnerability
A Windows system likely has a vulnerability if it lacks proper Local Security Policy configurations. It might use weak password requirements or lack account lockout thresholds. This allows attackers to perform brute-force attacks and gain unauthorized access to the system's credentials.

### Protection
Prevents brute-force and credential theft.

---

## Task 2: Enable BitLocker Encryption

![Screenshot](screenshots/windows/task2-bitlocker.png)

### Configuration Steps
1. Open the Start menu and search for "Manage BitLocker".
2. Select the drive you want to encrypt and click "Turn on BitLocker".
3. Choose how to back up your recovery key and follow the prompts to start encrypting.

### Vulnerability
A system without BitLocker likely has a vulnerability because the data is stored in plain text. If the physical device is stolen or compromised, this allows attackers to bypass the OS authentication process and gain direct unauthorized access to sensitive files.

### Protection
Prevents bypassing OS authentication physically.

---

## Task 3: Implement Windows Defender Firewall Rules

![Screenshot](screenshots/windows/task3-defender-firewall.png)

### Configuration Steps
1. Search for "Windows Defender Firewall with Advanced Security".
2. Click on "Inbound Rules" or "Outbound Rules", then select "New Rule".
3. Follow the wizard to allow or block a specific connection/port, then save.

### Vulnerability
The target system likely has a vulnerability if Windows Defender Firewall rules are not strictly configured. It might allow unrestricted inbound and outbound traffic, which allows attackers to exploit active services or establish an unauthorized remote connection to the target's system.

### Protection
Stops service exploitation and remote access.

---

## Task 4: Disable Unnecessary Services

![Screenshot](screenshots/windows/task4-disable-services.png)

### Configuration Steps
1. Open the Start menu and search for "Services" (or type `services.msc`).
2. Scroll through the list to find the targeted unnecessary service (e.g., Print Spooler or Xbox Live Auth Manager).
3. Right-click the service, select "Properties", change the "Startup type" to "Disabled", and click "Stop".

### Vulnerability
A Windows system likely has a vulnerability if it runs unnecessary background services. It might provide additional entry points that are unmonitored. This allows attackers to exploit active but unused services to execute malicious code and gain unauthorized access to the target's system.

### Protection
Reduces total attack surface area.

---

## Task 5: Disable Unused Ports

![Screenshot](screenshots/windows/task5-disable-ports.png)

### Configuration Steps
1. Open "Windows Defender Firewall with Advanced Security".
2. Click on "Inbound Rules", then select "New Rule" on the right panel.
3. Select "Port", specify the unused port number (e.g., 445 or 23), select "Block the connection", and apply it to all profiles.

### Vulnerability
A system with active but unused ports likely has a vulnerability because it provides unnecessary entry points. It might leave open paths to internal services. This allows attackers to establish unauthorized connections, perform automated scanning, and gain backdoor access to the target's system.

### Protection
Stops automated scanning and backdoor attempts.

---

## Task 6: Configure User Account Control (UAC)

![Screenshot](screenshots/windows/task6-uac.png)

### Configuration Steps
1. Open the Start menu and search for "Change User Account Control settings".
2. Move the slider up to the highest level: "Always notify me when apps try to install software or make changes to my computer".
3. Click "OK" and confirm the change.

### Vulnerability
A system with weak UAC configurations likely has a vulnerability. It might allow malicious software to execute administrative tasks in the background without the user's knowledge. This allows attackers to perform silent malware installations and make unauthorized changes to the target's system.

### Protection
Prevents unauthorized installations.

---

## Task 7: Enable Audit Policies

![Screenshot](screenshots/windows/task7-audit-policies.png)

### Configuration Steps
1. Open "Local Security Policy" (`secpol.msc`).
2. Navigate to Local Policies > Audit Policy.
3. Double-click on policies such as "Audit logon events" or "Audit account management", check both "Success" and "Failure" boxes, and click "OK".

### Vulnerability
A system without proper audit policies likely has a vulnerability because it lacks the logs needed to track suspicious activities. It might fail to record successful and failed login attempts. This allows attackers to perform brute-force attacks and gain unauthorized access without being detected early on.

### Protection
Enables early detection of brute-force attacks.

---

## Task 8: Apply Microsoft Group Policy Security Settings

![Screenshot](screenshots/windows/task8-group-policy.png)

### Configuration Steps
1. Open the Start menu and type `gpedit.msc` to open the Local Group Policy Editor.
2. Navigate to Computer Configuration > Windows Settings > Security Settings.
3. Apply the required hardening policies (e.g., restricting software installation or enforcing password complexity) and close the editor.

### Vulnerability
A system without strict group policies likely has a vulnerability due to loose security configurations. It might allow regular users to alter critical settings easily. This allows attackers to exploit dangerous misconfigurations and bypass the centralized security baseline to gain unauthorized control over the system.

### Protection
Enforces a strict centralized security standard.
