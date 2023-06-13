# Ansible

Ansible is an open-source automation tool that simplifies the management and orchestration of IT infrastructure. It allows you to automate tasks such as configuration management, application deployment, and cloud provisioning.

Project Homepage: [Ansible is Simple IT Automation](https://www.ansible.com/)
Documentation: [Ansible Documentation](https://docs.ansible.com/)

## Introduction

Ansible uses a declarative language called YAML (Yet Another Markup Language) to describe the desired state of a system, and it communicates with remote systems over SSH or other remote management protocols.

## Key Features

- **Automation**: Ansible enables the automation of various IT operations, including system administration, network automation, cloud infrastructure management, and application deployment.
    
- **Playbooks**: Playbooks are configurations written in YAML that describe a series of tasks to be executed on remote systems. They specify the desired state of your infrastructure.
    
- **Push-based Model**: Ansible uses a push-based model, where it connects to the target systems and pushes the necessary configurations and commands to achieve the desired state.
    
- **Simplicity**: Ansible has a shallow learning curve and does not require the installation of agents or additional software on remote systems.
    
- **Idempotency**: Ansible emphasizes idempotency, allowing you to run the same playbook multiple times without causing unintended changes if the desired state has already been achieved.
    
- **Community**: Ansible has a large and active community that contributes to its development, maintains a vast library of pre-built automation modules, and shares best practices and knowledge.
    

## Ansible Tower

In addition to the open-source version, Ansible offers Ansible Tower, a commercial product that provides a web-based interface, role-based access control, job scheduling, and additional features for enterprise-scale automation.

## Conclusion

Ansible is a powerful automation tool that simplifies IT infrastructure management. Its use of YAML, push-based model, and emphasis on simplicity make it popular among system administrators, DevOps teams, and IT professionals in various domains.

---
## Using Ansible for the First Time

1. Install Ansible *(for Debian/Ubuntu)*:
```bash
sudo apt install ansible
```
*Note: You don't need to install **Ansible** on all of your servers/machines, you only need to install it on your main machine in which you will be managing the remote machines.*

2. Create an [**SSH key**](OpenSSH.md) and copy it to all servers you will be managing using **Ansible**.

3. Create a new [**Git repository**](Git.md) with name `ansible-confs`, then create an **inventory** file within this directory:
```bash
touch ~/dev/ansible-confs/inventory
```

4. Add your servers **IP addresses** or **Host Names** inside the **inventory** file:
```bash
192.168.2.6
192.168.2.39
hostname.local
```

5. Add, commit and push the changes to **GitHub**.

6. Test the connection between the main machine and the servers:
```bash
ansible all --key-file ~/.ssh/ed25519 -i inventory -m ping
```
**Command Explanation**:
	- `ansible`: It is the command-line tool used to execute Ansible commands and manage infrastructure automation.
	- `all`: It specifies the target hosts or groups on which the command will be executed. In this case, "all" means that the command will be applied to all hosts defined in the inventory.
	- `--key-file ~/.ssh/ed25519`: It specifies the location of the SSH private key file (`ed25519`) to be used for authentication when connecting to the remote hosts.
	- `-i inventory`: It specifies the path to the inventory file that contains the list of hosts or groups to manage. The inventory file defines the hosts' connection details, such as IP addresses, hostnames, SSH ports, and other variables.
	- `-m ping`: It specifies the Ansible module (`ping`) to be executed on the target hosts. In this case, the `ping` module is used to check the reachability of the hosts. The `ping` module sends a test command to the hosts and verifies if they respond, indicating that they are accessible.
Overall, the given command runs the `ping` module on all hosts defined in the inventory file, using SSH key-based authentication with the specified private key file. This command helps **verify the connectivity and availability of the hosts** in the inventory.

7. Create `ansible.cfg` in the main directory and add default `inventory` and `private_key_file` to it:
```bash
nano ansible.cfg
```
Add the **default** values:
```bash
[dfaults]
inventory = inventory
private_key-file = ~/.ssh/ed25519
```
*Note: This file will overwrite or have more priority than the main ansible `ansible.cfg` file found in `/etc/ansible`*

8. Now to can run the command in step *6* without specifying the **SSH key** or the **inventory** file:
```bash
ansible all -m ping
```

---
## Ansible Commands

|Command|Usage|
|---|---|
|`ansible-playbook`|Executes Ansible playbooks to automate complex tasks on remote hosts.|
|`ansible`|Executes ad-hoc commands or tasks on remote hosts defined in the inventory.|
|`ansible-galaxy`|Manages roles, collections, and other external content for Ansible.|
|`ansible-vault`|Encrypts and decrypts sensitive data files used in Ansible playbooks.|
|`ansible-doc`|Displays documentation for Ansible modules.|
|`ansible-config`|Displays or modifies Ansible configuration settings.|
|`ansible-lint`|Checks Ansible playbooks for best practices and potential issues.|
|`ansible-console`|Provides an interactive Ansible console for testing and debugging tasks.|
|`ansible-pull`|Retrieves and applies Ansible configurations from a version control system.|
|`ansible-inventory`|Displays the configured inventory of hosts and their attributes.|
|`ansible-vault encrypt`|Encrypts a file with Ansible Vault for securing sensitive data.|
|`ansible-vault decrypt`|Decrypts an encrypted file encrypted with Ansible Vault.|
|`ansible-vault edit`|Opens an encrypted file for editing with Ansible Vault.|
|`ansible-vault create`|Creates a new encrypted file using Ansible Vault.|
|`ansible-vault rekey`|Changes the encryption password for an existing encrypted file.|
|`ansible-vault view`|Displays the contents of an encrypted file without decrypting it.|
|`ansible-galaxy init`|Initializes a new Ansible role or collection directory structure.|
|`ansible-galaxy install`|Installs roles or collections from Ansible Galaxy or other sources.|
|`ansible-galaxy remove`|Removes installed roles or collections from Ansible Galaxy or other sources.|
|`ansible-galaxy import`|Imports roles or collections from external sources into Ansible Galaxy.|
|`ansible-galaxy search`|Searches for roles or collections in Ansible Galaxy.|

---
## Most Used Ansible Commands

| Command                    | Usage                           |
| -------------------------- | ------------------------------- |
| `ansible all --list-hosts` | Shows you a list of your hosts. |
| `ansible all -m gather_facts`                           |                                 |
