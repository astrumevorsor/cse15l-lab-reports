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

V basically means vert/invert.


example 1 with output

![img](https://i.imgur.com/LsFV0M7.png)


example 2 with output

![img](https://i.imgur.com/QC6RQWL.png)


## Counting instances

```
grep -c <string> <filename>

```


C here stands for count. 

Returns the number of lines that contain the pattern, instead of displaying the matching lines. (manual paraphrased from chatGPT)


examples and output

![img](https://i.imgur.com/uGXFSFF.png)



## Recursive find limited path

```
grep -r -l <string> <filedirectory> 

```

a. R reads recursively and prints paths+contents

b. L limits output terminal to paths only (purple)


![img](https://i.imgur.com/ZglcuF4.png)





## String find 

``` 

grep <string> <filename>


```

Returns the instances of given string in the concerned file. 


example 1 


![](https://imgur.com/mBtSrV6.png)

output


![](https://imgur.com/kiEATYG.png)



example 2



![](https://imgur.com/XXcyDBS.png)


output

![](https://imgur.com/XU8os60.png)

