# CS 193 Lab 5 - Secure Shell (SSH) and Aliases
The purpose of this lab is to teach basics about using the terminal and how to log into Purdue's CS machines through your own laptop.

**If you need help or have questions during any part of this lab please ask questions! We're here to help you!**

### Getting Started
In order to start working on this lab, you're going to first clone this repo.

**In this lab you will be submitting a file called 'answers.txt'. You can either edit this file locally and then push the file to your repo or you can edit the file directly on github.**

### What is SSH'ing
SSH is a secure/encrypted communication connection between two different machines - essentially its just a way to communicate with a different computer.

##### Scenario
Let's say its December and -5°F outside and you need to work on a project on the lab machines in Lawson. Instead of walking over in the cold you can just ssh to get access to the Lawson machine's terminal and code using vim.

##### SSH Command
To use the ssh command type in ssh and then the machine's name. If you want to ssh into any Lawson machine from your personal computer open up your terminal and type `ssh YOUR_CS_USERNAME@data.cs.purdue.edu` and press enter (if you are on a Lawson machine then run `ssh data.cs.purdue.edu`). Then, you'll be prompted for your Purdue CS password and once it's been entered you're in! You can now access any file on the Lawson machines through the command line.

### Aliases
Aliases are a great way to abbreviate and make custom terminal commands. Let's say you want to ssh into a machine in Lawson but don't want to type the entire ssh command every time. Making an alias is a great way to shorten the ssh command. The command to make an alias is
```
alias <CUSTOM_ALIAS>="<REAL_COMMAND>"
```

Let's go through an example where we want to shorten the command `ssh data.cs.purdue.edu` to `connect`.
Open Terminal and run the following command:

```
alias connect="ssh data.cs.purdue.edu"
```
**Note: This lab assumes you are on a Lawson machine. If not, your alias will look like `alias connect="ssh USERNAME@data.cs.purdue.edu"`
 where USERNAME is your Purdue username**

After running that command, if you run ``connect`` you will be prompted for your password. Since we made this alias through the command line, once you restart your terminal the alias will disappear. If you want to make an alias just once and have it be saved every time you open up the terminal, create the alias in your shell's rc file. For the purpose of this lab, use bash. Run `echo $0` to see which shell you are using and if it's not bash run `bash` to switch over.

#### .bashrc
The .bashrc file is located in your home directory and is just a script which gets run everytime you open a new instance of bash.
Go to your home directory and open up your .bashrc with your favorite text editor and put `alias connect="ssh data.cs.purdue.edu"` at the very bottom.

Now run `source .bashrc` in your home directory to restart the bash script. Now you can run `connect` and be able to ssh!

## Tasks:
Make two aliases in your .bashrc. Put the alias in answers.txt and describe what each of them do and how they are helpful.


#### How to Submit:
Commit and push answers.txt!

### Extra Fun

##### Setting up SSH keys:

You may have noticed that every time you pull or push to GitHub, you have to enter your username and password. This is because you are using the HTTPS protocol to connect to GitHub as a remote.

This has a few advantages:

* It's easier and faster to set up.
* It will still work on strict firewalls and proxies such as those restricting
  all ports but port 80 and 443 (only HTTP and HTTPS traffic).

The downsides being:

* You have to enter your credentials every time you push or pull.
* Typing your password can be insecure on unfamiliar machines or HTTP
  connections

Luckily, there is another way. You can set up the remote to use SSH instead of
HTTPS.

SSH uses RSA encryption. This allows you use a "password-less log in" using a
public/private key pair.

There is a great tutorial by GitHub on how to set up and use this method
[here](https://help.github.com/articles/generating-ssh-keys/).

Note: you will need to add an SSH key for every different machine you want
to clone on (e.g. your personal machine and the CS servers).
