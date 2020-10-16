# Vagrant_Kali

This is my set up for a base Kali Linux Pentesting VM - Automated using Vagrant and Ansible. It Uses the official [Hashicorp Vagrant Box](https://app.vagrantup.com/kalilinux/boxes/rolling) and currently only runs on VirtualBox. The default credentials for vagrant machines are shown below:

| Username  | Password  |
|---|---|
| vagrant  | vagrant |

## Setup

In order to run the Vagrant file, you need the following:
* [Vagrant](https://www.vagrantup.com/)
* [VirtualBox](https://www.virtualbox.org/)
* [Guest Addition Plugin for Vagrant](https://www.serverlab.ca/tutorials/virtualization/how-to-auto-upgrade-virtualbox-guest-additions-with-vagrant/)
* [Ansible](https://www.ansible.com/)

### Running with Ansible on host

Once you have the required items installed, you can download the `VM_Setup` configuration and simply run the following terminal command:

```bat
vagrant up
```

### Running without Ansible on host 

If you are running it from Windows or if you would prefer to have the Ansible scripts run from the Kali machine itself, I have included `VM_Setup_Contained` to do that for you. The main difference is that Vagrant will place the playbooks onto the Kali Vagrant Desktop and run them from there after installing Ansible on the Kali machine. Within the Ansible playbooks, the first 2 lines also changed - It replaces the `hosts: all` with the following:

```yaml
- hosts: localhost
  connection: local
```

## Configuration Files

The installation makes use of 2 Ansible playbooks and 2 configuration files:

| File  | Description  |
|---|---|
| setup_playbook.yml  | The Setup Playbook updates the Kali VM and installs tooling that I find useful. |
| software_playbook.yml  | The Software Playbook downloads general software that I make use of during pentests and some basic scripts. |
| bash_aliases  | Creates a few simple bash aliases from scripts that I created which I generally make use of.  |
| tmux_config  | My Tmux configuration file which includes tmux-logging. |

### Installed Software
The following software has been installed with the base image:

| Software  | Description  |
|---|---|
| [Visual Studio Code](https://code.visualstudio.com/) |  Visual Studio Code is a free source-code editor.  | 
| [Tmux](https://github.com/tmux/tmux/wiki) | Tmux is a terminal multiplexer that lets you switch easily between several programs in one terminal, detach them (they keep running in the background) and reattach them to a different terminal. |
| [SecLists](https://tools.kali.org/password-attacks/seclists) |  SecLists is a collection of multiple types of lists used during security assessments. |
| [Neo4j](https://neo4j.com/) | Neo4j is a native graph database which leverages not only data but also data relationships. Neo4j connects data as it’s stored. |
| [BloodHound](https://github.com/BloodHoundAD/BloodHound) | BloodHound uses graph theory to reveal the hidden and often unintended relationships within an Active Directory environment.  | 
| [Remmina](https://remmina.org/) | Remmina is a remote desktop client for POSIX-based computer operating systems. It supports the Remote Desktop Protocol, VNC, NX, XDMCP, SPICE and SSH protocol. | 
| [Golang](https://golang.org/) | Go is an open source programming language which is useful when creating offensive payloads. |
| [Gobuster](https://tools.kali.org/web-applications/gobuster) | Gobuster is a directory/file and DNS busting tool written in Go. |
[ [CrackMapExec](https://github.com/byt3bl33d3r/CrackMapExec) | CrackMapExec (a.k.a CME) is a post-exploitation tool that helps automate assessing the security of large Active Directory networks. |

### Cloned Repositories
The following repositories are cloned into the `/opt` directory:

| Repository  | Description  |
|---|---|
| [SysInternals](https://docs.microsoft.com/en-us/sysinternals/) | SysInternals contains advanced system utilities and technical information. | 
| [JAWS](https://github.com/411Hall/JAWS) | JAWS is PowerShell script designed to help penetration testers (and CTFers) quickly identify potential privilege escalation vectors on Windows systems. |
| [LinEnum](https://github.com/rebootuser/LinEnum) | Similar to JAWS, LinEnum is a script designed to help penetration testers (and CTFers) quickly identify potential privilege escalation vectors on Linux systems. |
| [PingCastle](https://github.com/vletoux/pingcastle) | Ping Castle is a tool designed to assess quickly the Active Directory security level with a methodology based on risk assessment and a maturity framework. |
| [Rubeus](https://github.com/GhostPack/Rubeus) | Rubeus is a C# toolset for raw Kerberos interaction and abuses. | 
| [SIET](https://github.com/Sab0tag3d/SIET) | SIET attempts to exploit Cisco Smart Install which is a plug-and-play configuration and image-management feature that provides zero-touch deployment for new switches. |
| [Mitm6](https://github.com/fox-it/mitm6) | Mitm6 is a pentesting tool that exploits the default configuration of Windows to take over the default DNS server.  |
| [WindowsExploitSuggester](https://github.com/bitsadmin/wesng) | WES-NG is a tool based on the output of Windows' systeminfo utility which provides the list of vulnerabilities the OS is vulnerable to, including any exploits for these vulnerabilities. |
| [Covenant](https://github.com/cobbr/Covenant) | Please go to the link for details on how to use it. To run the application, you can use the following: `cd /opt/Covenant/Covenant && dotnet run` | 
| [PowerSploit](https://github.com/PowerShellMafia/PowerSploit) | PowerSploit is a collection of Microsoft PowerShell modules that can be used to aid penetration testers during all phases of an assessment. |
| [Postman](https://www.postman.com/) | Postman is a collaboration platform for API development which can be used during penetration assessments while focusing on APIs. | 
| [PrivEsc](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite) | Includes LinPeas and WinPeas privilege escalation tools for Windows and Linux/Unix*. |
| [RustScan](https://github.com/RustScan/RustScan) | Wrapper to increase the speed of Nmap scans.|

### Bash Aliases

The `.bash_aliases` file includes the following scripts that I created. The file can be modified as required to include additional aliases or remove the ones I added.

| Repository  | Description  |
|---|---|
| [ion](https://github.com/KyhleOhlinger/PentestScripts/blob/master/Bash%20Scripts/network.sh) | Simple Networking script to reset network driver and ping Google's primary DNS server.| 
| [zone](https://github.com/KyhleOhlinger/PentestScripts/blob/master/Bash%20Scripts/zone.sh) | Simple Zone Transfer Bash Script. |
| [ldap-query](https://github.com/KyhleOhlinger/PentestScripts/blob/master/Bash%20Scripts/ldap.sh) | LDAP bash script for domain enumeration. |
| [shell](https://github.com/KyhleOhlinger/PentestScripts/blob/master/Bash%20Scripts/tty_shell.sh) | Basic commands to upgrade to TTY Shell. |

## Recent Additions
* Created empty optical drive to install Guest Additions
* Added vagrant user to vboxsf group `sudo usermod -G vboxsf -a vagrant` - grants access to shared folders
* Added in CrackMapExec

## Future Work
* Add in VMWare as a provider option
* Create a Base Windows VM build with similar functionality.
* Port functionality to a Parrot OS version.

## Follow Me

<img height="32" width="32" src="https://github.com/StackExchange/Stacks-Icons/blob/production/src/Icon/GitHub.svg" /> [Github: KyhleOhlinger](https://github.com/KyhleOhlinger)

<img height="32" width="32" src="https://github.com/StackExchange/Stacks-Icons/blob/production/src/Icon/LinkedIn.svg" /> [LinkedIn: Kyhle Ohlinger](https://za.linkedin.com/in/kyhleohlinger)

<img height="32" width="32" src="https://github.com/StackExchange/Stacks-Icons/blob/production/src/Icon/LogoGlyphMd.svg" /> [StackOverflow: Kyhle Ohlinger](https://stackoverflow.com/users/5114477/kyhle-ohlinger)

<img height="32" width="32" src="https://github.com/StackExchange/Stacks-Icons/blob/production/src/Icon/Twitter.svg" /> [Twitter: KyhleO](https://twitter.com/KyhleO)
