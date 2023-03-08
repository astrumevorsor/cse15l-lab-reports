
## Step 1: Setup: Delete any existing forks of the repository you have on your account

First, access your github homepage from 

```https://github.com/<your username here>```

And go to your repositories. Access the forked repository from your repos.

![img](https://i.imgur.com/auwvsnH.png)

Go to settings and delete your repository. 

![img](https://i.imgur.com/nNrQc3c.png)

Moreover, use ```ls``` and ```rm -rf lab7``` in your terminal to delete your repo. 

![img](https://i.imgur.com/mBO2bb5.png)


## Step 2: Setup: Fork the repository

Go to search and jump to the respository [Link](https://github.com/ucsd-cse15l-w23/lab7) 

![img](https://i.imgur.com/LmYwvg4.png)

Fork this repo. 

![img](https://i.imgur.com/ibEZTH3.png)


## Step 3: Log into ieng6

The CLDQ way of doing this is just using the up arrow, Or ```ctrl+r``` on windows. 
Usually, from previous logins you have a history. 

On my mac, I usually go with up key, but during skill demos, no point checking ```ctrl+r```, as tutors would usually erase the history.

![img](https://i.imgur.com/NWiPkSv.png)

Use your password from your clipboard. In the demo there is no password, so again there's no point. 

## Step 4: Clone your fork of the repository from your Github account

The moment you login, use ```ctrl+r```, even on mac. Search git and then you'll find the most recently run command, for me this 
was ```git clone https://github.com/ucsd-cse15l-w23/lab7```. Easy. Now, run the command pressing the return key. 

Keys pressed: ```<ctrl + r> <g> <i> <t> <return>```

![img](https://i.imgur.com/d6NYyrL.png)


## Step 5: Run the tests, demonstrating that they fail

Change directory to lab7, just search ```cd```, my most recent one was lab7, so it was convenient to use ```ctrl+r```
Now use ```ctrl+r``` and check the junit tests. The first result on me typing j was ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` and I pressed return. Saved a lot
of time. 

Then, I also pressed ```ctrl+r``` and used java space, which led me to the runtime of the junit class. 

There was one failure in total.

![img](https://i.imgur.com/iD4CSqF.png)

Keys pressed: ```<ctrl + r> <c> <d> <return> <ctrl +r> <j> <return> <ctrl+r> <j><a><v><a> <space> <return>```


## Step 6: Edit the code file to fix the failing test

Open your ssh ieng6 from VsCode after opening the remote extensions from the command palette. This is ```F1``` on windows 
or ```shift + cmd + p ``` on mac. Connect to ieng6. Now, edit the code. Save using ```ctrl+s ```

![img](https://i.imgur.com/kpRBn9l.png)

Keys pressed:

``` <shift + cmd + p> <s> <s> <h> <ctrl + c> to copy password <ctrl+v> for pasting. <1> <backspace> <2> <ctrl+s> to code```

## Step 7: Run the tests, demonstrating that they now succeed

Run the junit tests again. javac should be 2 arrows up and the run tester should be 2 arrows up. Run these tests. 

Should be okay now. 

![img](https://i.imgur.com/KLkQcpN.png)

Keys pressed: ```<up> <up> <return> <up> <up> <return>```

## Step 8: Commit and push the resulting change to your Github account

Again, search for ```git add```. It is surely there in your command history. ```ctrl + r``` then search ```git a```, should display ```git add```.
Same way search ```git c```. Commit the changes to your repo. We're done. 

Keys pressed: ``` <ctrl+r> <g><i><t> <space> <a> <return> <ctrl+r> <g> <i> <t> <space> <c> <return> ```


![img](https://i.imgur.com/N8W3OX2.png)
