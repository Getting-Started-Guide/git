# Getting Started With SSH Keys & Git 

### Guide 

```sh
$ eval `ssh-agent -s`
``` 


1. Create SSH key. 

```sh
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
``` 


2. Set up Git & SSH in the shell. 

```sh
$ ssh-add C:\Users\<name>\.ssh\id_ed25519
// OR
$ ssh-add ~/.ssh/id_ed25519
$ Identity added: C:\Users\<name>\.ssh\id_ed25519

$ ssh-add -l
``` 


3. Register SSH key on Github. 

> To do this, run the following command and copy the output string to your clipboard. 

```sh
$ type C:\Users\your_user_name\.ssh\id_rsa.pub
``` 


4. Set up Github in the shell. 

```sh
$ TODO 
$ git config --global core.sshCommand "C:/Windows/System32/OpenSSH/ssh.exe"
``` 


5. Testing GitHub SSH connection. 

```sh
$ ssh -T git@github.com
``` 


6. Signing the GitHub commits. 

> Install PGP: https://www.gnupg.org/download/

```sh
$ gpg --full-generate-key 

// short version
gpg --list-secret-keys 

// long version
gpg --list-secret-keys --keyid-format LONG 

// show pgp-key
/Users/<name>/.gnupg/secring.gpg
------------------------------------
sec   4096R/LU5S31I6DHNBY7VX 2022-01-01 [expires: 2022-12-31]
uid                          <name> 
ssb   4096R/1PLFLPSD4VQNQS31 2022-01-01

// <LU5S31I6DHNBY7VX> would be the gpgp-key
gpg --armor --export YOUR_GPG_KEY 

``` 



### Tips and Tricks

 - If the default 2048-bit RSA keys are too weak, you can create stronger keys with the following commands:

```sh
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
$ ssh-keygen -t ecdsa -b 521 -C "your_email@example.com"
$ ssh-keygen -t ed25519 -C "your_email@example.com"
``` 

 - Win10 Work arounds:

[Microsoft Windows Help](https://docs.microsoft.com/de-de/windows-server/administration/openssh/openssh_keymanagement) 
[Microsoft Windows Help (CACHE)](https://web.archive.org/web/20211225232019/https://docs.microsoft.com/de-de/windows-server/administration/openssh/openssh_keymanagement) 

```sh 
// Automate Windows password prompt
1. Windows-Dienstverwaltung
2. Öffne die Eigenschaften des Dienstes OpenSSH Authentication Agent, stelle den Starttyp auf Automatisch (Verzögerter Start) und bestätige mit OK.
3. Starte den Dienst OpenSSH Authentication Agent.

// Alternative: 
$ Get-Service ssh-agent | Set-Service -StartupType Automatic -PassThru | Start-Service 

// Passphrase this also applies across reboots 
ssh-add $env:userprofile\.ssh\id_rsa 
``` 

```sh 
// SSH with Git for Windows 
1. Öffne den Windows-Explorer. 
2. Klicke mit der rechten Maustaste auf Dieser PC und klicke im Kontextmenü auf Eigenschaften. 
3. Klicke auf Erweiterte Systemeinstellungen. Ein Dialogfenster öffnet sich. 
4. Klicke auf die Schaltfläche Umgebungsvariablen. 
5. Unter Benutzervariablen für <Name Deines Rechners> klicke auf Neu. 
6. Trage folgenden Werte ein: 
        Name der Variablen = GIT_SSH 
        Wert der Variablen = C:\Windows\System32\OpenSSH\ssh.exe 
7. Bestätige alle Dialoge mit OK. 
// Alternative: 
$ git config --global core.sshCommand C:/Windows/System32/OpenSSH/ssh.exe 
``` 

```sh 
// UNTESTED: experimental explorative approach 
$ ssh-add -l 
// if empty 
$ ssh-agent -s 
$ ssh-add ~/.ssh/id_rsa 
$ eval `ssh-agent -s`
``` 

Win Temp Solution
```sh 
$ ssh-add -l
=> leer
$ ssh-agent -s
$ ssh-add ~/.ssh/id_ed25519_no_passphrase
$ eval `ssh-agent -s`
$ git clone git@github.com:.........git
``` 
