*This project has been created as part of the 42 curriculum by suyoun.*

# Born_2_be_root

## Description


The **Born_2_be_root** project is a system administration and virtualization exercise that focuses on setting up and securing a Linux virtual machine.

The **objective** of this project is to create a virtual machine with a secure operating system configuration while learning about system administration, virtualization, user management, networking, security, and monitoring.

This project introduces important concepts such as:

* Virtual machines and virtualization
* Linux system administration
* User and group management
* SSH
* Sudo
* Password policies
* Firewall configuration
* Disk partitioning and LVM
* AppArmor
* Cron jobs
* System monitoring
* Security practices

The virtual machine is configured according to the requirements of the Born2beroot subject and is intended to provide a secure and controlled Linux environment.

---

## Instructions

**Virtual Machine**

The project is implemented using a virtual machine.

- Virtualization: VirtualBox
- Operating System: Debian
- Architecture: x86_64
- Hostname: YOUR_HOSTNAME

The virtual machine can be started through VirtualBox and accessed through the configured user account.

**User Management**

A regular user is created for daily use and belongs to the required groups.

The current user and groups can be checked with:
```
whoami
id
groups
```

Administrative operations are performed using sudo rather than directly logging in as the root user.

**SSH**

SSH is configured to allow secure remote access to the virtual machine.

The SSH service can be checked with:
```
sudo systemctl status ssh
```
The configured SSH port can be checked with:
```
sudo ss -tulpn | grep ssh
```

The SSH configuration can be found in:
```
/etc/ssh/sshd_config
```
**Firewall**

A firewall is configured to restrict incoming network connections.

The firewall status can be checked with:
```
sudo ufw status verbose
```

Only the required ports are allowed.

**Password Policy**

A password policy is configured to enforce secure passwords.

The configuration includes requirements such as:

* Minimum password length
* Password expiration
* Password expiration warning
* Password history
* Character requirements

Relevant configuration files include:
```
/etc/login.defs
/etc/pam.d/common-password //i think i didnt change in there check the git repo guide u followed
```

The current password policy can be inspected through these configuration files.

**Sudo**

Sudo is configured to allow authorized users to execute administrative commands while applying security restrictions.

The sudo configuration can be checked with:
```
sudo visudo
```
The current user's sudo permissions can be checked with:
``
sudo -l
```

**Disk Partitioning and LVM**

The virtual machine uses partitions and Logical Volume Management (LVM).

The partition layout can be checked with:
```
lsblk
```

LVM information can be inspected using:
```
sudo pvs
sudo vgs
sudo lvs
```

These commands display the physical volumes, volume groups, and logical volumes configured on the system.

**Monitoring**

A monitoring script is configured to periodically display information about the system.

The monitoring information includes:
- Operating system and kernel
- CPU architecture
- CPU usage
- RAM usage
- Disk usage
- CPU load
- Last boot time
- LVM status
- Active TCP connections
- Logged-in users
- Network information

The monitoring script can be executed manually to verify that it is working correctly.

**Cron**

The monitoring script is executed periodically using cron.
The cron configuration can be checked with:
```
sudo crontab -l
```
The cron service can be checked with:
```
sudo systemctl status cron
```
**AppArmor**

AppArmor is used to provide an additional layer of security by restricting the capabilities of selected applications.

Its current status can be checked with:
```
sudo aa-status
```
---

## Algorithm Explanation and Justification

Unlike a traditional programming project, Born2beroot does not primarily focus on implementing an algorithm.

The main objective is to design and configure a secure Linux environment while understanding how the different system components work together.

The configuration process can be summarized as follows:

Create and install the Linux virtual machine.

Configure the hostname and system settings.

Create the required users and groups.

Configure a secure password policy.

Configure sudo with the required restrictions.

Configure SSH for secure remote access.

Configure and enable the firewall.

Partition the disk using the required LVM configuration.

Configure AppArmor.

Create the monitoring script.

Configure cron to execute the monitoring script periodically.

Test and verify each configuration.

Security Approach

The main security principle of the project is to minimize unnecessary access and privileges.

Administrative access is controlled through sudo, network access is restricted using the firewall, SSH access is configured explicitly, and password policies are used to enforce stronger authentication requirements.

LVM is also used to organize the storage into logical volumes, allowing the filesystem layout to be managed independently of the physical disk.

---

## Resources

Debian documentation

Linux man pages

VirtualBox documentation

UFW documentation

AppArmor documentation

42 Born2beroot subject

Discussions with 42 Peers

Useful Commands

The following commands are useful when checking the configuration of the virtual machine:
```
hostnamectl
uname -a
whoami
id
groups
lsblk
df -h
free -m
ip addr
ss -tulpn
sudo ufw status verbose
sudo systemctl status ssh
sudo systemctl status cron
sudo aa-status
sudo pvs
sudo vgs
sudo lvs
```

### AI Usage

AI tools (such as ChatGPT) were used in this project for:

Clarifying Linux and system administration concepts

Understanding SSH, sudo, firewall, and LVM configuration

Understanding password policies and security requirements

Debugging configuration issues

Explaining Linux commands and their output

Reviewing the README structure and documentation

No AI-generated configuration was used without understanding and manually verifying it. All system configurations were tested and validated manually on the virtual machine.

---

## Additional Notes

Born2beroot is an important introduction to system administration and virtualization.

The project provides practical experience with Linux security, networking, storage management, user permissions, automation, and system monitoring.

The virtual machine should be tested regularly to ensure that all required services and security configurations are working correctly.

Before evaluation, the configuration should be verified directly on the virtual machine rather than relying only on the documentation.

---