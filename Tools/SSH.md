# Secure Shell Protocol

## Adding a new SSH key

### Creating a new **SSH key** of type `ed25519`:
```bash
ssh-keygen -t ed25519 -C "your comment"
```

- `-t` flag is used to specify the type of the **key pair** you want to generate, **SSH** supports different types of **key pairs** for authentication. The most commonly used types of SSH keys are:
	1. `RSA` (Rivest-Shamir-Adleman): `RSA` keys are widely supported and commonly used for SSH authentication. They provide good security and performance.
    
	2. `DSA` (Digital Signature Algorithm): DSA keys are another type of asymmetric encryption algorithm used for SSH authentication. However, they are less commonly used compared to `RSA` keys.
    
	3. `ECDSA` (Elliptic Curve Digital Signature Algorithm): `ECDSA` keys use elliptic curve cryptography and offer smaller key sizes compared to `RSA` keys while providing the same level of security. They are increasingly popular due to their efficiency and security.
    
	4. `Ed25519`: `Ed25519` keys are based on the `EdDSA` (Edwards-curve Digital Signature Algorithm) scheme. They offer strong security and good performance. Ed25519 keys have become more popular in recent years due to their simplicity and resistance to certain types of attacks.
---
### Copying the **public SSH key** to the **server**:
1. If you are using **Linux** as the **Client**:
```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub 192.168.2.39
```
*note: **SSH** assumes by default that the username on the **server** is the same as your workstation (**client**). If not, add `<username>@` in front*

2. If using **Windows** as the **Client**:
- Copy the **public SSH key** to the server using `scp`:
```powershell
scp C:\Users\ahmed\.ssh\id_ed25519.pub aelzagh@192.168.2.39:/home/aelzagh/.ssh/authorized_keys
id_ed25519.pub
```
- Make sure that the `.ssh` folder is created before on the **server**.
- Access the **server** and give the right permission to `.ssh` folder and `authorized_keys` file:
```bash
sudo chmod 700 ~/.ssh
sudo chmod 600 ~/.ssh/authorized_keys
```
- If you have another **SSH key/s** on the **server**, copy the contents of `id_ed25519.pub` from the **client** machine and add it as a new line in `~/.ssh/authorized_keys` on the **server**.
---
### Using a specific  **SSH key** for connection:
- Specify the location and the name of the **private SSH key** you want to use by adding the `-i` option followed by it's location:
```bash
ssh -i ~/.ssh/id_ed25519 aelzagh@192.168.2.39
```
---
### Caching your passphrase on a **Linux Client**:
- Allows you to use a SSH key secured with a **passphrase** without entering the **passphrase** each time you connect to the **server**:
```bash
eval $(ssh-agent) && ssh-add
```

- How does it work?
	1. It works by running the `ssh-agent` process in the background which will cache your **passphrase** when you enter it for the first time to be used afterwards.
	 
	2. The `ssh-add` command adds your **SSH private key** to the **SSH agent**. By adding your private key to the agent, you can use it for authentication without having to re-enter the **passphrase** every time you connect to an **SSH server**.
	 
	3. It's important to note that running this command **only** sets up the SSH agent **for the current session**. If you want to persist the agent across terminal sessions, you may need to configure it to run automatically when you log in or start your system.
