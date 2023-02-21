# Using the grep command in different ways 

For lab report 3, I shall be using the grep command. 

To start, use ```grep man``` on the bash shell and see any commands of interest.

## Inverted matching: 

format:

```
grep -v <string> <filename> 

```

I prompted chatGPT to give me an example of the use of this command, this basically gives us the lines of that file which 
do not demonstrate the required pattern. 

The -v option can be useful when you want to exclude certain lines from the command line output. For example, you might use it to exclude comments or headers from a data file. This basically serves as a filter for certain filenames as well and file types. It is very useful while searching for specific file types which do not belong to the type we inverted. 

V basically means vert/invert.


example 1 with output- filtering out filenames with bahamas in them; basically shows whatever filenames do not contain the word bahamas. 

![img](https://i.imgur.com/LsFV0M7.png)


example 2 with output- filtering out any and all files without .txt in them, showing whatever files there were in skill demo with these properties. 

![img](https://i.imgur.com/QC6RQWL.png)


## Counting instances

```
grep -c <string> <filename>

```


C here stands for count. 

Returns the number of lines that contain the pattern, instead of displaying the matching lines. (manual paraphrased from chatGPT)

Whenever we want to search a large file/document, we usually find the particular patterns/filename patterns, create a document called find-results.txt and then use grep on it to filter the output, then cast it to grep-results.txt and use wc. Such a tedious procedure is long enough to type, let alone run on a terminal. To remove this redundancy we use grep -c, the command to count the file pattern, where we can directly access the count of the pattern we want.  

examples and output- in one image here

example 1 is where we are trying to see which files have Bahamas in them, and we run this command to get output 4. So, 4 files are about bahamas in this directory. 

example 2 is where we are trying to see which files are txt format, we get 225 as the output, hence 225 files are .txt format here. You can see these below. 

![img](https://i.imgur.com/uGXFSFF.png)



## Recursive find limited path

```
grep -r -l <string> <filedirectory> 

```

a. R reads recursively and prints paths+contents

b. L limits output terminal to paths only (purple)

grep -r -l is the command we used in the skill demo, of course. It is the combination of 2 commands, -r and -l where we basically want to limit ourselves to the given directory, which is treated as a dataset- we can see the contents of this directory and this directory ONLY. We must specify whatever string we wish to search for and then it will recursively, i.e. just like functions in CSE11, run this command over all the files in the directory and print only those files which contain this arbitrary string. For eg, Find the txt file in that directory that has the course-specific username you were provided at the start of the demo; task 11. We need to use grep -r -l <course username> <skill demo directory> here. This command throws errors if you mention non existent directories. Be careful.

  
Examples and output: (Both are in the same image)
  
Example 1 is from the skill demo, of course, it is the task where we have to find all the files containing lucayans string. We MUST restrict ourselves to skill-demo1-data/ as this is the local directory where we are supposed to find those txt files. 
  
Example 2 is from experimentation, we try and find all the files containing India string. Again we restrict ourselves here to skill demo directory. Notice that there is a weird non txt file at the beginning. To remove it, just use --include= ".txt" before -l and bingo, we are done.

![img](https://i.imgur.com/ZglcuF4.png)





## String find 

``` 

grep <string> <filename>


```

Grep searches the instances of the given string in that concerned file and returns them. Classic use of the grep command where we try and search for any string in a concerned file and want to leave out the others.


example 1: Trying to find all the text files which are there in this directory, use find, create a file containing the results of find and then use grep to filter out any non-txt file. (Lab week 4)


![](https://imgur.com/mBtSrV6.png)

output


![](https://imgur.com/kiEATYG.png)



example 2: Trying to find all files which contain string bahamas. 



![](https://imgur.com/XXcyDBS.png)


output

![](https://imgur.com/XU8os60.png)

