# How to Generate SSH Keys on a Windows Machine

## To Generate SSH Key Pair in Windows

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
- To read the public and private keys
   - open `GitBash` 
   ```bash
   cd .ssh/  # Change directory to the hidden SSH configuration folder in the user's home directory.
   cat id_ed25519     # To read/view Private Key
   cat id_ed25519.pub # To read/view Publick Key
   ``` 

![gitbash view](Images/sshkeys5.png)

- AWS and Azure expect keys to be stored or used from here.
***

# How to Configure Locally Generated SSH Keys for AWS and Azure VMs on Windows?

## Configuring Locally Generated SSH Keys for AWS and Azure VMs on Windows (as shown in below image)

![keys to aws and azure](Images/sshkeys3.png)

***

# How to Configure Locally Generated SSH Keys for AWS EC2 Instances on Windows?

### To configure locally generated SSH keys for AWS EC2 instances on Windows.

- Login: [aws.amazon](https://aws.amazon.com/free/) 

![sign up to console](Images/awsaccount1.1.png)

- click on `Sign in using root user email`(as shownin in below image) 

![aws root user login page](Images/awsaccount2.png)

# Import SSH Key(Public key) to AWS Account (for EC2 launch)

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

- finally it looks as shown in the below image.

![keypairs section](Images/awsssh5.png)

## Summary:

### Importing the Public Key to AWS
1. Log into AWS Management Console.
2. Go to EC2 Dashboard.
3. Under "Network & Security," click on **Key Pairs**.
4. Click **Import Key Pair**.
5. Provide a name for your key pair.
6. Open your public key file (`id_ed25519.pub`) in a text editor.
7. Copy the entire contents of the public key file.
8. Paste the copied key into the **Public key contents** field.
9. Click **Import** to save the key pair.
***

**NOTE:**
- **When launching an EC2 instance, your imported key pair appears in the Key pair dropdown under the Key pair section of the launch wizard. This lets you select it during configuration before final launch.**
***


## How to Launch AWS Ubuntu Instance with Imported Key

1. Open AWS Management Console and go to EC2 Dashboard.

2. Click **Launch Instance**.

![ec2 to launch instances](Images/ec2aws1.png)

3. Select an Ubuntu Server AMI (e.g., Ubuntu 20.04 LTS or Ubuntu 24.04 ).

![choosing ubuntu ami](Images/ec2aws2.png)

4. Choose the instance type (e.g., t2.micro for free tier).

![choosing instance type](Images/ec2aws3.png)

5. Click **Next** to configure instance details as needed.

6. In the **Key Pair** section, select the imported SSH key pair from the dropdown.

![selecting import keypair](Images/ec2aws4.png)

7. Configure security group to allow SSH (port 22) access from your IP address.

8. Review and click **Launch** to start the instance.

![launching instance](Images/ec2aws5.png)

9. Wait for the instance to enter the "running" state.

10. Note the public IP address of the instance for SSH access.

![Launching instance](Images/ec2aws6.png)

11. To connect to Instance, Open Terminal and run the command

``` bash
 ssh ubuntu@43.204.98.223
```
![login to instance](Images/ec2aws7.png)




***


# Steps to Import SSH Public Key via Azure Portal

- To import an existing SSH public key into your Azure cloud account using the Azure Portal follow these steps.


1. **Sign In**
   - Log in to the [https://azure.microsoft.com](https://portal.azure.com) with your account credentials.

![login to azure portal](Images/azure_ssh01.png)

## Create Resource Group Using Azure Portal

1. In the left-hand menu, select **Resource groups** (or search "Resource groups" in the top search bar).

![creating resource group](Images/azure_ssh1.png)

2. Click **+ Create** or **+ Add** at the top.

![create](Images/azure_ssh2.png)

3. On the Create a resource group page:
   - **Subscription:** Select your Azure subscription.
   - **Resource group name:** Enter a unique name for the resource group.
   - **Region:** Select the Azure region where you want the resource group to reside.

4. Click **Review + create**.

5. After validation succeeds, click **Create**.

![choosing above all](Images/azure_ssh3.png)

6. The resource group was created successfully and the details are displayed as follows:

![click on review](Images/azure_ssh4.png)


2. **Navigate to SSH Key Management**
   - In the left menu or the search bar, type and select **SSH keys** or head to **Azure Home > SSH keys** (sometimes under "Security + Networking" or can be searched directly).


   ![searching ssh keys in azure](Images/azure_ssh5.png)

3. **Add SSH Key**
   - Click on **+ Add** or **Create** (may appear as “+ Add SSH key” or “+ Create SSH key”).


![alt text](Images/azure_ssh5.1.png)

4. **Configure SSH Key Details**

   - **Subscription:** Select your Azure subscription.
   - **Resource group** choose the **Resource group name** which you have created.
   - **Region:** Select a region. Azure just stores the key metadata here; you can use the key in all regions.
   - **Key pair name:** Enter a meaningful, unique name for this key (for tracking and selection purposes).
   - **SSH public key source:** Choose “Upload existing public key” (not generate new).

5. **Paste the Public Key**
   - In the upload field, paste the entire contents of your existing SSH public key file (for example, contents of `id_rsa.pub` or `id_ed25519.pub`). (Remove any extra whitespace)

6. **Review + Create**
   - Click **Review + create**. Azure runs validation on the input.

![alt text](Images/azure_ssh6.png)

7. **Create and Finish**
   - Once validation passes, click **Create**. The SSH public key is now stored in your Azure account and available for assigning to virtual machines or other resources when needed.

***

### Additional Tips

- You can copy your public key again later by clicking on the key you uploaded and using the **Copy to clipboard** option.
- The uploaded public key can now be selected as an authentication method when creating or connecting to Linux VMs.
- At creation time for a VM, choose “Use existing key stored in Azure” to assign this imported public key.

***




