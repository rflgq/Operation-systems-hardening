# Part 2: Linux Server Hardening

Terminal-Based Security & Intrusion Detection

---

## Task 1: Disable Unnecessary Services

![Screenshot](screenshots/linux/task1-disable-services.png)

### Configuration Steps
```bash
# List active services
systemctl list-unit-files --state=enabled

# Stop the unnecessary service (e.g., apache2 or cups)
sudo systemctl stop <service_name>

# Disable it from starting on boot
sudo systemctl disable <service_name>
```

### Vulnerability
A Linux server likely has a vulnerability if it runs unnecessary background services. It might provide additional entry points that are unmonitored. This allows attackers to exploit active but unused services to execute malicious code and gain unauthorized access to the target's system.

### Protection
Prevents exploitation of unused active services.

---

## Task 2: Configure Firewall (UFW)

![Screenshot](screenshots/linux/task2-ufw-firewall.png)

### Configuration Steps
```bash
# Set default rules: deny incoming, allow outgoing
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Allow SSH so you don't get locked out
sudo ufw allow ssh

# Enable the firewall
sudo ufw enable

# Check status
sudo ufw status verbose
```

### Vulnerability
A server without a properly configured firewall likely has a vulnerability because it accepts all inbound network traffic. It might not filter dangerous requests, which allows attackers to scan for open ports and establish an unauthorized connection or execute a Denial of Service (DoS) attack.

### Protection
Prevents port scanning and DoS attacks.

---

## Task 3: Implement SSH Hardening

![Screenshot](screenshots/linux/task3-ssh-hardening.png)

### Configuration Steps
```bash
# Open the SSH configuration file
sudo nano /etc/ssh/sshd_config
```
Then edit the following directives:
```
# Change the default SSH port
Port 2222

# Disable root login
PermitRootLogin no

# Use key-based authentication instead of passwords
PubkeyAuthentication yes
PasswordAuthentication no
```
```bash
# Restart the SSH service to apply changes
sudo systemctl restart ssh
```

### Vulnerability
Default SSH configurations likely have a vulnerability because of a few factors. It might use the default port "22" and allow direct root access with password-based authentication. This allows attackers to perform automated brute-force attacks and gain direct root access to the target's system without requiring complex key credentials.

### Protection
Stops automated brute-force attempts.

---

## Task 4: Configure Automatic Security Updates (Ubuntu)

![Screenshot](screenshots/linux/task4-automatic-updates.png)

### Configuration Steps
```bash
# Install the unattended-upgrades package
sudo apt install unattended-upgrades

# When prompted, select "Yes" to automatically download and
# install stable security updates
```

### Vulnerability
A system without automatic updates likely has a vulnerability because it runs outdated software. It might lack the latest security patches for known bugs. This allows attackers to exploit these known vulnerabilities to bypass security measures and compromise the target's system.

### Protection
Stops exploit attempts on known system bugs.

---

## Task 5: Implement File Permission Restrictions

![Screenshot](screenshots/linux/task5-file-permissions.png)

### Configuration Steps
```bash
# Restrict a sensitive file (e.g., /etc/shadow) to owner-only read/write
sudo chmod 600 /etc/shadow

# Verify the change
ls -l /etc/shadow
```

### Vulnerability
A system with weak file permissions likely has a vulnerability because it might not implement strict access control. It might allow regular users to read or modify sensitive configuration files. This allows attackers to escalate privileges or extract critical data to manipulate the system structure.

### Protection
Prevents privilege escalation and data theft.

---

## Task 6: Implement Intrusion Detection (Fail2Ban)

![Screenshot](screenshots/linux/task6-fail2ban.png)

### Configuration Steps
```bash
# Install Fail2Ban
sudo apt install fail2ban

# Create a local config file to avoid overriding defaults
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local

# Start and enable the service to run on boot
sudo systemctl start fail2ban
sudo systemctl enable fail2ban
```

### Vulnerability
A server without an intrusion detection system such as Fail2Ban likely has a vulnerability. It might not monitor malicious activities or allow unlimited login attempts. This allows attackers to perform continuous brute-force attacks and guess user credentials to gain unauthorized access to the system.

### Protection
Stops persistent brute-force attempts from specific IPs.
