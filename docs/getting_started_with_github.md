# Getting Started With a new GitHub Project

### Guide

1. Create a new project on GitHub UI and a empty direction on your local maschine.

2. Decide if you want to use **HTTPS** or **SSL** as a protocol to establish a connection
   and replaced in the following part the variable `<CONNECTIONTYP>` with your chosen connection.
    > For **HTTPS** use: *https://github.com/`<OrganizationName or Username>`/`<RepositoryName>`.git*
    
    > For **SSL** use: *git@github.com:`<OrganizationName or Username>`/`<RepositoryName>`.git*

3. Initialize the new created project folder for git

```sh
$ echo "MY FIRST CONTENT IN README" >> README.md
$ git init
$ git add README.md
$ commit -m "first commit"
$ remote add origin <CONNECTIONTYP>
$ push -u origin master
``` 

### Tips and Tricks

 - If you have problems with the authentication with your IDE on your own maschine, you can set username and passwort in clear text unencrypted for authentication

```sh
$ git remote set-url origin https://<USERNAME>:<PASSWORD>@github.com/<OrganizationName or Username>/<RepositoryName>.git
``` 
