# week 6 - lab report 3
## by faith rivera
### may 8, 2022

--- 

## working across ssh and remote servers


<p align="center">
  <img src="https://64.media.tumblr.com/b39a0d08b328820d75b7e699dce49b89/tumblr_n1dkqfuJmZ1qc2xm1o1_500.gifv" width="2800">
</p>

We're back in the network! So far, we've learned about ssh keys, transferring data, and even how to make changes and debug our code. This week, we will dive further into improving our experience in connecting and exporting data and files across different computers.

As a preface: all work on this blog post is done on a **Mac** computer to work with the `ieng6` system. When connected to my `ieng6` account, it is done on Linux software. Thus, some commands can vary if your personal computer is a Mac or Windows device.

---

## 1: Streamline `ssh` Configuration
Although using a `ssh` key definitely speeds up the login process, we still must type in a long string similar to `$ ssh cs15lsp22zzz@ieng6.ucsd.edu`. It's still a lot to memorize! Luckily, using a `config` file allows us to speed up the process even more by sharing information about specific servers to our key.

To do so, we first ensure that we have a `config` file in our `ssh` folder.

 To check if you have a `config` file: 
 1. Change your directory to `ssh`: `cd ~/.ssh`
 2. Open `~/.ssh/config`. If you can't in the terminal, You can open it manualy through Mac Finder like I did in the photo below.
 ![check for config](cdconfig1.png)
 3. Add the following lines to your `config` file:
``` 
Host ieng6
HostName ieng6.ucsd.edu
User cs15lsp22zzz (use your username)
```
Refer to the photo below to match:
![config file lines](configlines.png)

The first line `Host` can be changed (from `ieng6` to something else) - this is what the computer uses to recognize where to log into. 

Once you save to the file, you should be able to type the following to log in with your `ssh` key becuase of the specific login domain and username you put in `config`:

`ssh ieng6`

The computer will thus log you in and display a message like below.
![configured login to ieng server](configlogin.png)

---

## 2. Set up Github Access from ieng6