# How to Generate and Use SSH Keys on Windows for AWS and Azure VMs?

## How to Generate SSH Keys on a Windows Machine
#### To Generate SSH Key Pair in Windows

- Open the Terminal or PowerShell.

- Run the command:
  ```bash
  ssh-keygen
  ```
  - Press Enter to choose the default file location (e.g., `C:\Users\YourUserName\.ssh\id_ed25519`).

![sshkeys generation](Images/sshkeys1.png)

  - Optional: Add a passphrase or leave blank for no passphrase.
- Your public key will be found at `C:\Users\YourUserName\.ssh\id_ed25519.pub`.

![listing keys in .ssh](Images/sshkeys2.png)


### Why SSH keys are in the `.ssh` folder

- `.ssh` is the default folder where SSH looks for keys.
- It keeps `keys` organized and safe.
![ssh keys in terminal and windows file explorer](Images/sshkeys4.png)
- Only you can access it, protecting your private key.
- AWS and Azure expect keys to be stored or used from here.
***
# Importing SSH Keys to AWS and Azure Cloud Accounts

![keys to aws and azure](Images/sshkeys3.png)


# Import SSH Key to AWS Account (for EC2 launch)

- Open AWS Management Console,
  - **Go to EC2** 

![open ec2](Images/awsssh1.png)
- In EC2 section, 
  - under `Network and security` 
    - **Click on `Key pairs`** 

![opening keypairs](Images/awsssh2.png)
- Choose "Import Key Pair".

![click on import keypair](Images/awsssh3.png)
- Enter a key pair name.(Name = your choice)
- Open your public key file (e.g., `id_ed25519.pub`) as shown in the below image(click on browse to open).
- To save Click on Import Key Pair.

![importing a new keypair](Images/awsssh4.png)

**NOTE:**
- When launching a new EC2 instance, select your imported key pair in the Key Pair section.

