# Lab Report 1 - Remote Access and Filesystem

## Part 1 - Set up a coding environment

First, we will be setting up a coding environment. It will provide a convenient way to use the terminal, which we will need to connect to the CSE remote servers for account access. Install [Visual Studio Code](https://code.visualstudio.com/) by clicking on the link, and follow the installation instructions on the site. After successful installation, open the application and you should see a screen like this:

## Part 2 - Set up your CSE15L account

Next, we will be setting up your CSE15L account which is what you will be using our remote servers. Visit this [link](https://sdacs.ucsd.edu/~icc/index.php), input your UCSD username and PID in the respective fields, and click submit. Under "Additional Accounts", you should see your CSE15L account username in the form `cse15lwi23***` where `***` is filled with your account-specific tag. Click on the username, and then click on the hyperlink that says "change your password". Again, input your username and PID and click subit. Input your current password (the one you use to log into your UCSD email), and then input a new password for your CSE15L account. Make sure your password is complex enough (and you can use your regular UCSD password if you'd like). Before submitting, make sure "Change MyTritonLink password?" is checked to "No". When you are ready to submit, click on the field where you confirmed your new password and then press enter/return. This will submit the password change request which should take effect within 15 minutes.

## Part 3 - Using the remote servers

Next, we will go over how to connect to the remote servers. For Windows users, `git` must be installed first. If you're using macOS like me then the tools we need are already installed and we can move on. Open a terminal in VS Code by clicking "Terminal", and then "New Terminal". Input the command `ssh cs15lwi23***@ieng6.ucsd.edu`, making sure to replace `***` with your username specific information. 
