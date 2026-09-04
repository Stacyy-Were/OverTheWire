# 1. LEVEL 0

The goal of this level is to log into the game using `SSH`. The host to which you need to connect is `bandit.labs.overthewire.org`, on port `2220`. The username is `bandit0` and the password is `bandit0`.

**Commands you may need to solve this level:**

```bash
ssh
```

The default SSH port is `22`. When using `ssh user@host`, SSH will try to connect through port `22`. Since this challenge uses port `2220`, we must specify the port number using `-p`.

```bash
ssh -p 2220 bandit0@bandit.labs.overthewire.org
```

Using the given password:

```text
bandit0
```

After running the command, we get access to the Bandit remote server.

---

# 2. LEVEL 0 - 1

### Level Goal

The password for the next level is stored in a file called `readme` located in the home directory.

Use this password to log in as username `bandit1` using SSH.

Whenever you find a password for a level, use SSH on port `2220` to log into that level and continue the game.

**Commands you may need to solve this level:**

```bash
ls
cd
cat
file
du
find
```

In the remote server, I used `ls -la` to list the files in the home directory and find the `readme` file.

```bash
ls -la
```

Then I used `cat` to read the contents of the file:

```bash
cat readme
```

This gave me:

```text
The password you are looking for is: 6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
```

I then connected to the host `bandit.labs.overthewire.org` using the username `bandit1` on port `2220`.

```bash
ssh -p 2220 bandit1@bandit.labs.overthewire.org
```

Password:

```text
6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
```

---

# 3. LEVEL 1 - 2

### Level Goal

The password for the next level is stored in a file called `-` (a dashed filename) located in the home directory.

**Commands you may need to solve this level:**

```bash
ls
cd
cat
file
du
find
```

In the home directory, I used `ls` to see the files:

```bash
ls
```

One of the files was named:

```text
-
```

I initially tried:

```bash
cat -
```

However, this did not work as expected because `cat -` interprets `-` as standard input (`stdin`) rather than as the filename.

I then used:

```bash
cat ./-
```

The `./` tells the shell that `-` is the name of a file in the current directory.

This gave me the password for the next level.

### PASS

**Password for Level 2 → 3:**

```text
PK8fYLZg2hnHSz83plBL1iEPKdD3QToB
```

I then connected to the next level using:

```bash
ssh -p 2220 bandit2@bandit.labs.overthewire.org
```

---

# 4. LEVEL 2 - 3

### Level Goal

The password for the next level is stored in a file called `--spaces in this filename--` located in the home directory.

**Commands you may need to solve this level:**

```bash
ls
cd
cat
file
du
find
```

Spaces in filenames can cause issues in the terminal because the shell treats spaces as separators between arguments.

For example:

```bash
cat my text.txt
```

The terminal will interpret `my` and `text.txt` as two different arguments rather than one filename.

These issues can be avoided by using a backslash `\` or quotation marks `""` in the terminal XD.

I used `find` to confirm the exact filename:

```bash
bandit2@bandit:~$ find "./--spaces in this filename--"

./--spaces in this filename--
```

I then used quotation marks around the filename so that the entire filename would be treated as a single argument:

```bash
bandit2@bandit:~$ cat "./--spaces in this filename--"

7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```

### PASS

**Password for Level 3 - 4:**

```text
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```

---

# 5. LEVEL 3 - 4

### Level Goal

The password for the next level is stored in a hidden file in the `inhere` directory.

**Commands you may need to solve this level:**

```bash
ls
cd
cat
file
du
find
```

I first SSH'd into `bandit3` using:

```bash
ssh -p 2220 bandit3@bandit.labs.overthewire.org
```

Using the password from the previous level:

```text
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```

After logging in, I used:

```bash
ls -la
```

to list all files and directories, including hidden ones.

This revealed the `inhere` directory.

I then entered the directory:

```bash
cd inhere
```

and used:

```bash
ls -la
```

to list all the files, including hidden files.

One of the files was:

```text
...Hiding-From-You
```

I then read the file using:

```bash
cat ./...Hiding-From-You
```

This gave me the password for the next level.

### PASS

**Password for Level 4 - 5:**

```text
xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq
```

---

# 6. LEVEL 4 - 5

### Level Goal

The password for the next level is stored in the only human-readable file in the `inhere` directory.

**Tip:** If your terminal is messed up, try the `reset` command.

**Commands you may need to solve this level:**

```bash
ls
cd
cat
file
du
find
```

 first SSH'd into `bandit4` using:

```bash
ssh -p 2220 bandit4@bandit.labs.overthewire.org
```

Using the password from the previous level:

```text
xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq
```

After logging into the bandit4 host `inhere` directory, I typed in `ls -la` to get info on the files and got nine files. Reading each file then got the password in `-file07`:
```bash
cat -- -file07
```
Getting the password for the next level
```
6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG
```

# 7. LEVEL 5 - 6
### Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
1. human-readable
2. 1033 bytes in size
3. not executable

**Commands you may need to solve this level:**

```bash
ls
cd
cat
file
du
find
```
SSH into bandit5 using:
```bash
ssh -p 2220 bandit5@bandit.labs.overthewire.org
```
Using the password we got from the previous level:
```text
6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG
```
After logging into bandit5 host `inhere` directory, I type din `ls -la` to get details on the available directories and files.

The level goal was to find the `bandit6` password in a human-readable file that is 1033 bytes and non-executable. IN the terminal I specified these features by typing in"
```bash
find . -type f -size 1033c
```
and the output was `./maybehere07/.file2/`. I then checked what type of file it was with the file command and the output was `./maybehere07/.file2: ASCII text, with very long lines (1000)` which tells us that the file is human-readable because it's ASCII text. I used the cat command to get the password.

Level 6 - 7 password:

```text
pXa26xhMWaC2SvDotA4r9EgZkulOeSBW
```
