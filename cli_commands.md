# sudo Commands in Linux

## What is sudo?

`sudo` means:

> Super User DO

It allows a normal user to run commands with administrator (root) permissions.

---

# sudo Commands

## Create New User

```bash
sudo adduser harsha
```

Creates a new user account.

---

## Add User to sudo Group

```bash
sudo usermod -aG sudo harsha
```

Gives sudo permissions to user `harsha`.

Explanation:
- `usermod` → modify user
- `-a` → append
- `-G` → group
- `sudo` → sudo group

---

## Check sudo Permissions

```bash
sudo -l
```

Shows sudo permissions of the current user.

`-l` means:
- `list`

---

## View sudo Group Members

```bash
sudo grep sudo /etc/group
```

Shows users present in the `sudo` group.

---

# Important sudo File

## `/etc/sudoers`

This file controls:
- who can use `sudo`
- what commands they can run

---

# View sudo Configuration

```bash
sudo cat /etc/sudoers
```

Displays sudo configuration file.

---

# Safe Way to Edit sudoers

```bash
sudo visudo
```

Safely edits `/etc/sudoers`.

Why?
- checks syntax errors
- prevents broken sudo configuration
- safer than direct editing

---

# Example sudoers Rule

```bash
%sudo ALL=(ALL:ALL) ALL
```

---

# Meaning of `ALL=(ALL:ALL) ALL`

Structure:

```bash
user/group HOST=(USER:GROUP) COMMANDS
```

| Part | Meaning |
|---|---|
| `%sudo` | users inside sudo group |
| first `ALL` | all hosts |
| `(ALL:ALL)` | all users and groups |
| last `ALL` | all commands |

Full meaning:

Users in `sudo` group can run all commands as any user/group on any host.

---
# Restrict sudo Permissions

## Restrict User

```bash
vasu ALL=(ALL) /usr/bin/apt update
```

`vasu` can run only:

```bash
sudo apt update
```

---

## Restrict Group

```bash
%developers ALL=(ALL) /usr/bin/git
```

Users in `developers` group can run only:

```bash
sudo git
```

`%` means group.
---

# 2. apt

## What is apt?

`apt` means:

> Advanced Package Tool

Used to:
- install software
- update packages
- remove packages

---

# Important apt Commands

| Command | Meaning |
|---|---|
| `sudo apt update` | Refresh package information |
| `sudo apt upgrade` | Install updates |
| `sudo apt install package` | Install software |
| `sudo apt remove package` | Remove software |
| `sudo apt autoremove` | Remove unused dependencies |
| `apt list --installed` | Show installed packages |

---

# Examples

## Update package info

```bash
sudo apt update
```

---

## Install tree

```bash
sudo apt install tree
```

---

## Upgrade packages

```bash
sudo apt upgrade
```

---

## Remove package

```bash
sudo apt remove tree
```
---

# 3. find

## What is find?

`find` is used to:

> search files and directories.

---

# Important find Flags

| Flag | Meaning |
|---|---|
| `-name` | Search by filename |
| `-iname` | Case insensitive search |
| `-type f` | Search only files |
| `-type d` | Search only directories |
| `-empty` | Find empty files |
| `-delete` | Delete found files |
| `-perm` | Search by permissions |


---
# Sample Commands for find Practice

## Create a folder and enter it

```bash
mkdir demo
cd demo
```

---

## Create files and folders

```bash
touch a.txt b.txt c.log d.txt
mkdir folder1 folder2
```

---

## Add content to files

```bash
echo "hello world" > a.txt
echo "linux find command" > b.txt
```

---

# find Command Examples

## Find txt files

```bash
find . -name "*.txt"
```

---

## Find directories

```bash
find . -type d
```

---

## Find files

```bash
find . -type f
```

---

## Find empty files

```bash
find . -empty
```

---

## Find large files

```bash
find . -size +10M
```

---

## Find and delete logs

```bash
find . -name "*.log" -delete
```
---

# 4. rsync

## What is rsync?

`rsync` is used to:

> copy and synchronize files/directories efficiently.

Main advantage:
- copies only changed files

---

# Important rsync Flags

| Flag | Meaning |
|---|---|
| `-a` | Archive mode |
| `-v` | Verbose output |
| `-r` | Recursive copy |
| `-h` | Human readable sizes |

---

# Examples

## Sync folders

```bash
rsync -av source/ backup/
```

---

## Recursive copy only

```bash
rsync -r source/ backup/
```

---

## Human readable output

```bash
rsync -avh source/ backup/
```

---

# Archive Mode

```bash
rsync -a
```

Preserves:
- permissions
- ownership
- timestamps
- links

---

# Difference Between cp and rsync

| cp | rsync |
|---|---|
| Copies everything | Copies only changed files |
| Mainly copy | Synchronization |

---

# 5. tree

## What is tree?

`tree` displays:
> files and directories in hierarchical structure.

Useful for:
- project visualization
- folder understanding

---

# Install tree

```bash
sudo apt install tree
```

---

# Important tree Flags

| Flag | Meaning |
|---|---|
| `-L` | Show limited levels |
| `-a` | Show hidden files |
| `-d` | Show directories only |
| `-f` | Show full path |
| `-I` | Ignore pattern |

---

# Examples

## Show directory tree

```bash
tree
```

---

## Show only 2 levels

```bash
tree -L 2
```

---

## Show hidden files

```bash
tree -a
```

---

## Show directories only

```bash
tree -d
```

---
