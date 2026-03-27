# How to create GitHub account

- [Refer Here](https://github.com/) to signup GitHub.

![GitHub Login Page](Images/github1.png)

- To create GitHub account, signup with `email` and create `username` 

![Create GitHub account](Images/github2.png)

- After creating github account login page will be like 

![github repo page](Images/github3.png)


***

# How to create a repository in GitHub (Remote Repository)

- Let's creat repository in Git and clone to local system/machine. 

- click on `Create repository` 

![creating repo in gitgub account](Images/github8.png)


- When creating a remote repository on platforms like **GitHub, GitLab, or Bitbucket**, the repository page displays **two clone URLs**: HTTPS and SSH.

## HTTPS URL Format
```
https://github.com/username/repository.git
```
- Uses username/password or personal access token (PAT) for authentication.
- Prompts for credentials on each push/pull (unless cached).
- Works everywhere without SSH setup.

## SSH URL Format
```
git@github.com:username/repository.git
```
- Requires SSH key setup (public key added to your account).
- Passwordless authentication via your private key.
- Faster/more secure for frequent operations.


![https and ssh](Images/github8.1.png)

## When to Use SSH vs HTTPS?

### Use **SSH** when:
- ✅ You're a **regular Git user** (daily pushes/pulls)
- ✅ **Corporate/personal machine** - one-time key setup  
- ✅ Need **maximum security** (keys > passwords)
- ✅ **Automation/CI/CD** pipelines
- ✅ No firewall blocking port 22

### Use **HTTPS** when:
- ✅ **Beginners** - simpler setup (no keys)
- ✅ **Corporate firewalls** block SSH (port 22)
- ✅ Working on **shared/public computers**
- ✅ **Quick testing** from new machines/instances/virtual mahcines
- ✅ Behind **proxies** that only allow port 443

### Quick Decision Table

| Scenario | SSH | HTTPS |
|----------|-----|-------|
| Daily development | ✅ **Recommended** | ❌ |
| Corporate firewall | ❌ | ✅ **Recommended** |
| Beginner friendly | ❌ | ✅ **Recommended** |
| Max security | ✅ **Best** | Good |
| One-time setup | More work | Easier |

****

# How to Clone a Remote Git Repository to Local Using SSH URL?

### usecase 1: cloning remote repo to local using SSH URL

- open Terminal, Create one folder and `cd into the folder`

```bash
mkdir githubpractice
cd githubpractice
git clone <SSH URL>
```

- after cloning cd into the `repo` (as shown in the below image)

```bash
cd entity
```
- If you're using Terminal/PowerShell, it looks like this:


![git clone](Images/github10.png)


- If you're using Git Bash, it looks like this:


![git clone and cd to repo](Images/github11.png)

- Now, in the repo try to 
    - `create some files` and 
    - `add` those files to files to staging area
    - `commit` all the changes

![github account](Images/github12.png)


#### Now, To push all the local changes to the git remote repo, we need to do some additional configurations

## Prerequisites for Pushing to Remote Repository

**Before your first `git push` to GitHub, complete these essential configurations:**

```
1. SSH Key Authentication (secure passwordless access)
2. Git User Identity (username & email for commits)  
3. Remote Origin Setup (link local repo to GitHub)
```

**Once configured → `git push origin main` works seamlessly.**

## 1. How to Add an `SSH Key to GitHub`? 

- Open settings and click on `SSH and GPG Keys`

![ssh and gpg keys](Images/github4.png)

- Then, Click on `NEW SSH Key`

![new sshkey](Images/github5.png)

- Add `public key` in the `key section` and give a `title`. 
    - click on `ADD SSH KEY`

![adding ssh key](Images/github6.png)


- you will see Succesfully congigured ssh keys to GitHub.


### NOTE

- [Refer Here](https://github.com/pnvenkatakrishna/sshkeys_setup/blob/main/sshkeyssetup.md) to understand **ssh keys generation**

- To add `public key`, open your `GitBash` and check as shown in the below image. 
![pub and private key to read](Images/sshkeys5.png)


## 2. How to configure GitHub `username` and `gmail` to your system

- To configure your `Git username and email`, use the `git config` command in your terminal or PowerShell. This sets your identity for commits across repositories or per repo.


### Global Configuration
- Run these commands to set your username and email system-wide `(stored in ~/.gitconfig on Linux/Mac` or `%USERPROFILE%\.gitconfig on Windows)`. 


```bash
git config --global user.name "Your User Name"

git config --global user.email "your.email@example.com"
```

![Replace placeholders with your details](Images/github7.png)

***

## Git Config Verification

```bash
# View all global settings
git config --global --list

# OR check specific values
git config --get user.name
git config --get user.email
```

***

## Test SSH Connection to GitHub

**Verify your SSH key works with GitHub:**

```bash
ssh -T git@github.com
```

**Expected output:**
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

**What it does:**
- Tests SSH connection without interactive shell
- Confirms your public key is correctly added to GitHub
- Shows your authenticated username

## 3. Set Up Remote Origin (First Time Only)

**"origin"** = Default name for your main remote repository.

**Steps:**

1. **Copy SSH URL** from GitHub repo → *Code* → *SSH*
   ```
   git@github.com:username/repo.git
   ```

2. **Add remote origin:**
   ```bash
   git remote add origin git@github.com:username/repo.git
   ```

3. **Verify remote:**
   ```bash
   git remote -v
   ```
   **Output:** `origin git@github.com:username/repo.git (fetch/push)`

4. **Push with upstream tracking:**
   ```bash
   git push -u origin main
   ```

**After first push:** Just use `git push` for future commits.



## How to Create & Push to GitHub Using HTTPS + PAT?

### Step 1: Create New Repository on GitHub
```
1. GitHub Dashboard → "New" button
2. Repository name: "my-project"  
3. DON'T initialize README → Create repository
4. Copy HTTPS URL: https://github.com/yourusername/my-project.git
```
![alt text](Images/gitpat1.png)


![alt text](Images/gitpat2.png)

### Step 2: Clone Repository Locally

![alt text](Images/gitpat3.png)

```bash
git clone https://github.com/yourusername/my-project.git
cd my-project
```

![alt text](Images/gitpat4.png)


### Step 3: Set Git User Identity (First Time Only)
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Step 4: Generate Personal Access Token (PAT)

####  Open settings

![settings and devolper settings](Images/gitpat5.png)

```
GitHub → Settings → Developer settings → Personal access tokens → "Generate new token"

```
![alt text](Images/gitpat6.png)

![alt text](Images/gitpat7.png)


#### give repo (Full control of private repositories) (as shown in the below image)

![alt text](Images/gitpat8.png)

```
Copy token: ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
**⚠️ Save securely - cannot view again**
```
![alt text](Images/gitpat9.png)




### Step 5: Create Files & Commit Changes
```bash
# Create sample files
echo "# My Python Project" > README.md
echo "print('Hello GitHub!')" > hello.py

# Stage & commit
git add .
git commit -m "Add initial Python app + README"
```

### Step 6: Push to Remote (Uses PAT)
```bash
git push origin main
```
**Terminal prompts:**
```
Username for 'https://github.com': yourusername  
Password for 'https://yourusername@github.com': ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Step 7: Verify Success
```
✓ [origin/main 8f2a3d4] Add initial Python app + README
✓ Success! Check GitHub - files are live.
```

### Future Workflow (No Re-Authentication)
```bash
# Edit file
echo "print('Updated code')" >> hello.py
git add . && git commit -m "Update hello message"
git push  # ✅ No prompts - cached automatically
```



# GitHub Forking and Syncing Guide

### Introduction
Forking creates a personal copy of a repository on your GitHub account for contributions or experiments. Syncing pulls updates from the original ("upstream") repo to keep your fork current. 

### Step 1: Fork the Repository
1. Go to the original repo on GitHub (e.g., `https://github.com/owner/original-repo`).
2. Click **Fork** in the top-right corner.
3. Select your account—the fork appears under `https://github.com/your-username/original-repo`. 

**Clone locally:** 
```
git clone https://github.com/your-username/original-repo.git
cd original-repo
```

### Step 2: Set Up Upstream Remote
Link to the original:  
```
git remote add upstream https://github.com/owner/original-repo.git
```
Verify: `git remote -v` (shows `origin` as your fork, `upstream` as original). [youtube](https://www.youtube.com/watch?v=XTolZqmZq6s)

### Step 3: Sync Upstream Changes
Whenever upstream updates:
1. Fetch: `git fetch upstream`
2. Checkout main branch: `git checkout main`
3. Merge: `git merge upstream/main` (fix conflicts if prompted).
4. Push to your fork: `git push origin main` [youtube](https://www.youtube.com/watch?v=XTolZqmZq6s)

**Web Alternative:** On your fork's GitHub page, click **Sync fork** > **Update branch**. [youtube](https://www.youtube.com/watch?v=XTolZqmZq6s)

### Troubleshooting
- **Conflicts?** Edit files, `git add .`, `git commit -m "Resolve conflicts"`, then push.
- **Detached HEAD?** Ensure you're on `main` or `master`.
- Repeat sync as needed for ongoing changes. [stackoverflow](https://stackoverflow.com/questions/7244321/how-do-i-update-or-sync-a-forked-repository-on-github)

### Best Practices
- Sync before starting new work.
- Use branches for your changes: `git checkout -b my-feature`. [docs.github](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork)

Save this as Markdown and render it (e.g., via GitHub or VS Code preview) for sharing. Let me know if you need it in another format like PDF code or expansions!