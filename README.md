## Installing and Uninstalling Software in Linux

### Overview

This lab focused on installing and removing software in Linux, as well as working with archived files.

During the lab, I practiced:

* Installing software using `dpkg`
* Resolving package dependencies using `apt`
* Verifying installed packages using `dpkg`
* Extracting `.tar` archives
* Creating `.tar` archives
* Installing software using `apt`
* Uninstalling software using `apt`
* Verifying software removal

---

### Objectives

By completing this lab, I practiced:

1. Installing Sublime Text using `dpkg`
2. Fixing dependencies using `apt`
3. Extracting & Creating a `.tar` archive
4. Installing 7-Zip using `apt`
5. Uninstalling GIMP using `apt`
6. Verifying software installation and removal

---

## 1. Installing Sublime Text

### Using `dpkg`

A `.deb` package containing Sublime Text was already available on the Linux machine.

The package was located at:

```text
/home/qwiklab/downloads/sublime-text_build-3211_amd64.deb
```

I installed the package using `dpkg`:

```bash
sudo dpkg -i /home/qwiklab/downloads/sublime-text_build-3211_amd64.deb
```

This demonstrates that `dpkg` can install a `.deb` package but does not automatically resolve all missing dependencies.

---

### Fixing Dependencies with `apt`

I used `apt` to fix the missing dependencies:

```bash
sudo apt install -f
```

When prompted, I entered:

```text
Y
```

to continue.

After the dependencies were installed, Sublime Text was successfully configured.

![1](https://i.imgur.com/7yfJSlx.png)

---

### Verifying Sublime Text

I verified the installation using:

```bash
dpkg -s sublime-text
```

![2](https://i.imgur.com/DuYWxuk.png)
 
The package information showed:

```text
Package: sublime-text
Status: install ok installed
Priority: optional
Section: editors
Installed-Size: 34033
Maintainer: Sublime HQ Pty Ltd <support@sublimetext.com>
Architecture: amd64
Version: 3211
Depends: libgtk-3-0
Description: Sublime Text is a sophisticated text editor for code, markup and prose
```

### Result

**Sublime Text was successfully installed.**

---

## 2. Extracting a `.tar` Archive

The next task was to extract a `.tar` archive.

The archive was located in:

```text
/home/qwiklab/downloads/
```

The archive was:

```text
extract_me.tar
```

### Navigate to the Directory

I used:

```bash
cd /home/qwiklab/downloads
```

### Extract the Archive

I extracted the archive using:

```bash
sudo tar -xvf extract_me.tar
```

![3](https://i.imgur.com/ucq1rq2.png)

The contents included:

```text
home/qwiklab/extract_me/
home/qwiklab/extract_me/great_job
```

### Result

The `.tar` archive was successfully extracted.

---

## 3. Creating a `.tar` Archive

After extracting the archive, I moved back to the home directory:

```bash
cd ~
```

The `/home/qwiklab/documents` directory contained three files:

```text
Earth
Mercury
Venus
```

I used `tar` to archive these files into `Planets.tar`:

```bash
tar -cvf Planets.tar --absolute-names /home/qwiklab/documents/Earth /home/qwiklab/documents/Mercury /home/qwiklab/documents/Venus
```

![4](https://i.imgur.com/PmFc8l2.png)

The resulting archive contained:

```text
/home/qwiklab/documents/Earth
/home/qwiklab/documents/Mercury
/home/qwiklab/documents/Venus
```

### Result

The three files were successfully archived into:

```text
Planets.tar
```

---

## 4. Installing 7-Zip

Linux software can also be installed using the `apt` package manager.

I installed 7-Zip using:

```bash
sudo apt install p7zip-full
```

When prompted, I entered:

```text
Y
```

to confirm the installation.

The installation included:

```text
p7zip
p7zip-full
```

---

### Verifying 7-Zip

I verified the installation using:

```bash
dpkg -s p7zip-full
```

![5](https://i.imgur.com/1wchaWC.png)

The output showed:

```text
Package: p7zip-full
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 4664
Maintainer: Robert Luberda <robert@debian.org>
Architecture: amd64
Multi-Arch: foreign
Source: p7zip
Version: 16.02+dfsg-8
```

### Result

**7-Zip was successfully installed.**

---

## 5. Uninstalling GIMP

GIMP was already installed on the Linux system.

I used `apt` with the `remove` argument to uninstall it:

```bash
sudo apt remove gimp
```

When prompted, I entered:

```text
Y
```

to confirm the removal.

![6](https://i.imgur.com/cl5amkC.png)

The output showed:

```text
The following packages will be REMOVED:
  gimp
```

The system then removed GIMP:

```text
Removing gimp (2.10.22-4+deb11u2) ...
```

---

### Verifying GIMP Removal

I verified that GIMP was no longer installed using:

```bash
dpkg -s gimp
```

![7](https://i.imgur.com/bZTEJn8.png)

The result was:

```text
dpkg-query: package 'gimp' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files.
```

### Result

**GIMP was successfully uninstalled.**

---

## 6. Commands Used

### Install a `.deb` package

```bash
sudo dpkg -i /home/qwiklab/downloads/sublime-text_build-3211_amd64.deb
```

### Fix dependencies

```bash
sudo apt install -f
```

### Verify Sublime Text

```bash
dpkg -s sublime-text
```

### Navigate to Downloads

```bash
cd /home/qwiklab/downloads
```

### Extract `.tar` archive

```bash
sudo tar -xvf extract_me.tar
```

### Return to home directory

```bash
cd ~
```

### Create `.tar` archive

```bash
tar -cvf Planets.tar --absolute-names /home/qwiklab/documents/Earth /home/qwiklab/documents/Mercury /home/qwiklab/documents/Venus
```

### Install 7-Zip

```bash
sudo apt install p7zip-full
```

### Verify 7-Zip

```bash
dpkg -s p7zip-full
```

### Uninstall GIMP

```bash
sudo apt remove gimp
```

### Verify GIMP removal

```bash
dpkg -s gimp
```

---

## 7. Key Concepts

#### `dpkg`

`dpkg` is a low-level Debian package management tool.

In this lab, it was used to:

* Install a `.deb` package
* Check package information
* Verify whether software was installed

---

#### `apt`

`apt` is a higher-level package management tool that can handle dependencies.

In this lab, it was used to:

* Fix missing dependencies
* Install 7-Zip
* Remove GIMP

---

## 8. `dpkg` vs `apt`

| Tool             | Purpose                                    |
| ---------------- | ------------------------------------------ |
| `dpkg`           | Low-level Debian package management        |
| `apt`            | Higher-level package management            |
| `dpkg -i`        | Installs a `.deb` package                  |
| `dpkg -s`        | Displays package information               |
| `apt install`    | Installs packages and handles dependencies |
| `apt remove`     | Removes packages                           |
| `apt install -f` | Fixes dependency problems                  |


---

## 9. Tar Archives

The `tar` command can be used to create and extract archives.

#### Extracting

```bash
sudo tar -xvf extract_me.tar
```

#### Creating

```bash
tar -cvf Planets.tar --absolute-names /home/qwiklab/documents/Earth /home/qwiklab/documents/Mercury /home/qwiklab/documents/Venus
```

The important options used here are:

| Option | Meaning              |
| ------ | -------------------- |
| `-x`   | Extract              |
| `-c`   | Create               |
| `-v`   | Verbose output       |
| `-f`   | Specify archive file |

---

## 10. IT Support Relevance

These skills are useful for IT support because technicians frequently need to:

* Install applications
* Remove applications
* Troubleshoot dependency problems
* Verify software installations
* Work with package managers
* Extract archived files
* Create archives
* Use Linux command-line tools
* Work with elevated privileges

Instead of relying only on a graphical interface, an IT support specialist can use the Linux CLI to perform administrative tasks efficiently.

---

## 11. Cybersecurity Relevance

Software management is also important in cybersecurity.

Security professionals need to understand:

* What software is installed on a system
* How packages are installed
* How packages are removed
* How dependencies work
* How to verify installed software
* How administrative privileges are used
* How files can be archived and extracted

Package management is particularly relevant when maintaining systems, applying updates, removing unnecessary software, and investigating installed applications.

---

## 13. Skills Demonstrated

* Linux command-line navigation
* Debian package management
* `dpkg`
* `apt`
* `.deb` package installation
* Dependency troubleshooting
* Software installation
* Software removal
* Package verification
* `tar`
* Archive extraction
* Archive creation
* 7-Zip installation
* Use of `sudo`
* Linux system administration fundamentals

---

## Conclusion

In this lab, I practiced installing and uninstalling software in Linux and working with archived files.

I successfully:

* Installed Sublime Text using `dpkg`
* Fixed its dependencies using `apt`
* Verified Sublime Text using `dpkg`
* Extracted a `.tar` archive using `tar`
* Created a `.tar` archive containing multiple files
* Installed 7-Zip using `apt`
* Verified the 7-Zip installation
* Uninstalled GIMP using `apt`
* Verified that GIMP was removed using `dpkg`

This lab strengthened my Linux command-line, package management, software administration, and file archiving skills.
