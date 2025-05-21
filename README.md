# PP5

## Goal

In this exercise you will:

* Use Git **locally** on your own machine: create branches, make commits, and merge them back.
* Set up and interact with a **bare** Git repository on an SSH‐accessible server (e.g. **vorlesungsserver**, or any machine you have SSH access to).
* Push and pull to/from **GitHub** and the **THGA GitLab** server.
* Practice **forking** an existing repo, making changes, and submitting a **Pull Request** (on GitHub) or **Merge Request** (on GitLab).

**Important:** Start a stopwatch when you begin and work uninterruptedly for **90 minutes**. Once time is up, stop immediately and document exactly where you had to pause.

---

## Workflow

1. **Fork** this repository
2. **Modify & commit** your solution
3. **Submit your link for Review**

---

## Prerequisites

* Several starter repos are available here:
  [https://github.com/orgs/STEMgraph/repositories?q=Git%3A](https://github.com/orgs/STEMgraph/repositories?q=Git%3A)
* Ensure you have **SSH access** to a remote server (e.g., “vorlesungsserver”).
* Throughout, consult Git’s built-in man-pages (`git help <command>`) for explanations and options.

---

## Tasks

### Task 1: Local Git – Branching & Merging

1. Create a new directory in your home directory and initialize a repository in it. 
2. In one of your cloned repos, initialize a new branch called `feature-1`.
3. On `feature-1`, create a file `feature.txt` containing a short description of what you’re doing.
4. Commit your changes, then switch back to `master` (or `main`), and merge `feature-1` into your `master`.
5. Resolve any merge conflicts (if they arise) by hand, then commit the merge. 

**Your Commands & Output**

```bash
# Paste here the sequence of git commands you ran
# and the relevant terminal output (e.g., branch listing, merge messages)
```
### sequence of git commands
```bash
mkdir PP5
cd PP5
git init
echo "Übung PP5: Lokales Git-Repository" > README.md
git add README.md
git commit -m "Initialer Commit für PP5"
git checkout -b feature-1
echo "Dies ist eine neue Funktion für feature-1 in Übung PP5" > feature.txt
git add feature.txt
git commit -m "Hinzufügen von feature.txt im Branch feature-1"
git checkout main
git checkout master
git merge feature-1
git branch
```
### Terminal-Output:

```bash
Initialized empty Git repository in C:/Users/metin/PP5/.git/
[master (root-commit) 420e99f] Initialer Commit für PP5
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
Switched to a new branch 'feature-1'
[feature-1 37a804b] Hinzufügen von feature.txt im Branch feature-1
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
error: pathspec 'main' did not match any file(s) known to git
Switched to branch 'master'
Updating 420e99f..37a804b
Fast-forward
 feature.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
  feature-1
* master
```


---

### Task 2: Bare Repository on an SSH Server

1. On your SSH server (e.g., “vorlesungsserver”), create a **bare** repo at `~/repos/myproject.git`:

   ```bash
   ssh youruser@vorlesungsserver \
     "mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare"
   ```
2. On your local machine, add it as a remote named `origin-ssh`:

   ```bash
   git remote add origin-ssh youruser@vorlesungsserver:~/repos/myproject.git
   ```
3. Push your `master` branch to `origin-ssh`, then clone it into a fresh directory to verify.

**Your Commands & Output**

```bash
# Paste here the push & clone commands and outputs
```
### Bare Repository auf dem SSH Server erstellen
```bash
ssh user56@128.140.85.215
mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare
exit

# Remote hinzufügen
git remote add origin-ssh user56@128.140.85.215:~/repos/myproject.git
git remote -v

# Master-Branch pushen
git push origin-ssh master

# Repository klonen
cd ~
git clone user56@128.140.85.215:~/repos/myproject.git
```
```
Output:
The authenticity of host '128.140.85.215 (128.140.85.215)' can't be established.
ED25519 key fingerprint is SHA256:RxMwhpDxDq2aHcMAnAUsHJmeWgVVmCkXQSJCkB8zu44.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '128.140.85.215' (ED25519) to the list of known hosts.
user56@128.140.85.215's password:
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
Initialized empty Git repository in /home/user56/repos/myproject.git/
logout
Connection to 128.140.85.215 closed.

origin-ssh   user56@128.140.85.215:~/repos/myproject.git (fetch)
origin-ssh   user56@128.140.85.215:~/repos/myproject.git (push)

Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 591 bytes | 28.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
To 128.140.85.215:~/repos/myproject.git
 * [new branch]      master -> master

Cloning into 'myproject'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (6/6), done.
```



---

### Task 3: GitHub & THGA GitLab

1. On [GitHub](github.com), create a new empty repo under your account named `myproject-gh`.
2. On [THGA GitLab](gitlab.thga.de), create a new project named `myproject-gl`.
3. In your local repository, add these as remotes:

   ```bash
   git remote add github  git@github.com:YOUR_USERNAME/myproject-gh.git
   git remote add gitlab  git@gitlab.thga.de:YOUR_USERNAME/myproject-gl.git
   ```
4. Push your `master` branch to both `github` and `gitlab` remotes.

> Hint: You are just adding two more bare-remotes to your already existing repository!

**Your Commands & Output**

```bash
# Paste here the remote‐adding & push outputs
```

---

### Task 4: Fork, Modify, and Pull/Merge Request

1. On GitHub, **fork** one of the repos from the STEMgraph org.
2. Clone your fork locally, create a branch `pp5-changes`, and make a small change (e.g., update the README).
3. Commit and push `pp5-changes` to **your** fork, then open a **Pull Request** against the original repo.
4. Repeat on THGA GitLab: fork another students repository, clone, branch, change, push, and open a **Merge Request**. If your peers opened a merge request to your repository, review and merge or decline it!

**Your PR/MR Links & Descriptions**

* GitHub PR: *paste URL and a one-sentence summary*
* GitLab MR: *paste URL and a one-sentence summary*

---

**Remember:** Stop working after **90 minutes** and record where you stopped!
