# CSE 15L W23 Lab - Week 1 Report
## Part 1 Install/Open Visual Studio Code
Go to your OS’s start menu, type VSCode in the search bar and open VSCode. 


If you do not have VScode installed, click here to get the latest installation version for your OS. 

![Image](https://imgur.com/zkb6Cly)

Choose the file path where you want to install. This is a public PC, so I went with my user ID and installed it in the appdata local programs folder. You could install it on desktop as well, wherever you want, just make sure you remember your path as VSCode uses that path as your working directory.

Upon installation, launch VSCode. 



This is how it looks. 


Part 2– Remotely Connecting

CSE15L uses course specific accounts, with their own passwords and usernames. 

Format is cs15lxxabc@ieng6.ucsd.edu
xx is your quarter code and abc is your cse15l course username. 
To look it up, use the account lookup tool. You should ideally find your cse15l username over there. 




Now, reset the password for the cse15l account. This should be an easy to remember yet strong password combination. Please note, this will also reset your passwords for AD emails if you are signed into your student account, so keep your passwords handy. 



Open Terminal- this can be accessed from the terminal tab or the … icon on later versions of VSCode. 
Click on the new terminal icon. This opens a new terminal shell. Check the terminal shell for a dollar sign $. If not present, you must install git for windows so as to access bash commands, such as ssh. 

Installation for git is pretty straightforward, just remember to set VScode as the git default directory and set the git settings to use from the command line. 

Change terminal from powershell to gitbash


Login with your credentials that you set up after changing your password. 

The prompt “The authenticity of host 'ieng6.ucsd.edu (128.54.70.238)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.     
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])?” should be answered to by yes.

I have used cse rather than cs15l here, as I have authenticated the host on my terminal before. 








This remote connects you to the linux ieng ucsd servers. 
Beware about the password, as it delayed me many times and it was very frustrating to re enter it. Moreover, the format of mail is cs15l not cse15l.


Part 3 – Run Some Commands

Here are some specific useful commands to try:
cd ~ : changes directory to the home directory
cd: changes to the current directory
pwd: gives the absolute path of the current directory 
ls - lists all the files in the current directory 
ls <directory> where <directory> is /home/linux/ieng6/cs15lwi23/cs15lwi23abc, where the abc is one of the other group members’ username- where you will try to access the other students directory.
cp /home/linux/ieng6/cs15lwi23/public/hello.txt ~/
cat /home/linux/ieng6/cs15lwi23/public/hello.txt


You will be denied access to other students' directories by the administrator.

ls -lat is a useful way to see all the active linux tools. 

Whenever you cannot find a directory you will get such a prompt: NO such file or directory. When the cd command works, generally means that the directory is accessible to the user and exists. No prompt is given out. 



Once done with commands press ctrl+d to exit ieng from the git shell. Logout and close your computer. 
