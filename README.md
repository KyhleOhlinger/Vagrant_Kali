# Vagrant_Kali

This is my set up for a bare bones Kali Linux VM - Automated using Vagrant and Ansible. It Uses the official [Hashicorp Vagrant Box](https://app.vagrantup.com/kalilinux/boxes/rolling) and currently only runs on VirtualBox.

## Setup

In order to run the Vagrant file, you need the following:
* [Vagrant](https://www.vagrantup.com/)
* [VirtualBox](https://www.virtualbox.org/)
* [Guest Addition Plugin for Vagrant](https://www.serverlab.ca/tutorials/virtualization/how-to-auto-upgrade-virtualbox-guest-additions-with-vagrant/)

Once you have the required items installed, you can simply run the following terminal command:

```bat
vagrant up
```

## Additional Files

The installation makes use of 2 Ansible playbooks and a .bash_aliases file:

| File  | Description  |
|---|---|
| setup_playbook.yml  | The Setup Playbook updates the Kali VM and installs tooling that I find useful. |
| software_playbook.yml  | The Software Playbook downloads general software that I make use of during pentests and some basic scripts. |
| bash_aliases  | Creates a few simple bash aliases from scripts that I created which I generally make use of.  |

## Follow Me

<img height="32" width="32" src="https://github.com/StackExchange/Stacks-Icons/blob/production/src/Icon/GitHub.svg" /> [Github: KyhleOhlinger](https://github.com/KyhleOhlinger)

<img height="32" width="32" src="https://github.com/StackExchange/Stacks-Icons/blob/production/src/Icon/LinkedIn.svg" /> [LinkedIn: Kyhle Ohlinger](https://za.linkedin.com/in/kyhleohlinger)

<img height="32" width="32" src="https://github.com/StackExchange/Stacks-Icons/blob/production/src/Icon/LogoGlyphMd.svg" /> [StackOverflow: Kyhle Ohlinger](https://stackoverflow.com/users/5114477/kyhle-ohlinger)

<img height="32" width="32" src="https://github.com/StackExchange/Stacks-Icons/blob/production/src/Icon/Twitter.svg" /> [Twitter: KyhleO](https://twitter.com/KyhleO)
