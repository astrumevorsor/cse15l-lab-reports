# Lab 5: Using the find command on terminal command shell (MAC OS)

In the Lab 3, I used the ```grep``` command. Hence, 

I will research now the ```find``` command, an easy to use command on terminal. 

Similar to last time, type ```find man``` to pull up the find manual on command line. 

## Command 1- finding files by directory

### format and usage

To return the contents of a directory, if a certain directory simply exists and have files/folders in the directory, we use the ```find``` command in the following format. 

```find <directory path>```

This basically returns, if it exists, a large ordered output containing the directory path itself, with its full contents sorted on the basis of ASCII order.

### Advantages

1. You can search and check if a directory just exists and get the contents plus directory. 
2. It can be combined with other commands such as ```less``` or ```grep``` as seen in the previous skill demo, to refine the search.

### Disadvantages

1. It will always display a large number of results for larger directories.
2. Only filenames are searched and not the contents as in ```grep```. It is too broad a command and must be refined for specific searches.
3. The filename itself is contained and as you will see in these examples, this leads to errors while counting how many files we have overall in the directory. 


To elaborate on the above, let us see some examples. 

### Example 1

```find skill-demo1-data```

This returns all the files in skill-demo1-data, and the file skill-demo1-data itself. 

![Image](https://i.imgur.com/NWEw0DQ.png)

Look at how long the output is! Oh my god. I wish there was something that could help us. Oh wait, there is!

Use ```less find skill-demo1-data``` This groups all your files under their respective folders and outputs them.

![Image](https://i.imgur.com/cCuwru8.png)

### Example 2

```find skill-demo1-data> find-results.txt```


This casts the output of Example 1 to a file find-results.txt, stored in skill-demo1-data. Another solution to the absolutely absurd length of the output returned by our default find command. 

![Image](https://i.imgur.com/NWEw0DQ.png)

Use ```less find-results.txt``` command to just view a glance of your file's contents. This is the output.


![Image](https://i.imgur.com/Az6tciX.png)


## Command 2- finding files by name 


### format and usage

To check if a certain directory with a certain filename type simply exists or enlist the filenames of a particular format, we use the ```find``` command in the following format. 

```find <directory path> -name <format>```

```name``` is the filter here. It must be in string format.

This basically returns, if it exists, a large ordered output containing the files containing that pattern format sorted on the basis of ASCII order, and all its contents.

It is a recursive search over all the nodes in a filesystem that match the name entered in the command. 

### Advantages
1. You can search and check if a file type exists in that folder or if a filename exists in that folder.
2. It can be combined with other commands such as ```less``` or ```grep``` as seen in the previous skill demo, to refine the search.


### Disadvantages
1. Similar to example 1, output can be absurdly long.
2. Only filenames and not their contents are searched.

### Example 1

``` find skill-demo1-data -name "*.txt" ``` 
This command basically is an example of me trying to find all the text files in the skill demo1 directory. 

It was pretty cool to have a command as powerful as this one, the difference between ```grep``` and this is that ```grep``` is a little more inclined towards the recursive search and reading the contents of the files, while this cannot search up the contents if I wanted to. 

![Image](https://i.imgur.com/0xW4E3g.png)


### Example 2
``` find skill-demo1-data -name "WhatToLasVegas.txt"``` 
This command basically is an example of me trying to find a specific text file in this directory. Feels nice to have a small output for a change.  


![Image](https://i.imgur.com/wNqdBei.png)


## Command 3- finding files by type

### format and usage

To check if a certain file type exists in the directory, we use this command. 

```find <directory path/keyword> -type <format>```

```tyoe``` is the filter criteria.

This basically returns, if it exists, an ordered output containing the specific instances of the directory that satisfy the type we require. This ```type``` is a single letter format. 

It is a recursive search over all the nodes in a filesystem based on their object type. 

### Advantages
1. You can filter out specific file types from your search and this really works as a watertight substitute for the name searching command, where you always input a string. Here, the file type that you want is strictly treated as a parameter. 
2. Like every other ```find``` command, you can use combinations with other commands and do some really useful stuff with it. 

### Disadvantages
1. You must know your file types and documentations, which is not possible for a large dataset with random files.
2. You cannot see file contents.

### Example 1

If you remember example 1 from command 1, you know that there were directories too without the files, in the output returned. This is a counter for that situation. We can filter out directories by using the following command. 

```find skill-demo1-data -type f```

![Image](https://i.imgur.com/Xtq9cW8.png)

Notice the error I made initially. This command is highly case sensitive and you must know your filetypes really well.


### Example 2

Suppose now I want a list of all the directories within a directory. No problem!

```find skill-demo1-data -type d ```

Now we have all the directories!!

![Image](https://i.imgur.com/sAkVOzp.png)





## Command 4- finding files by size

### format and usage

To check if a certain directory has a file that is of a specific size, we use the ```find``` command in the following format. 

```find <directory path/keyword> -size <+ or -> <file size and suffix>```

```+``` means larger than
```-``` means less than
```size``` is the filter we use here

You can combine the ```size``` to have a specific range, by combining ```-a``` and ```+b``` where size(a)>size(b)

It is a recursive search over all the nodes in a filesystem based on their parameter size.

### Advantages
1. This is exceptionally useful with applications where we are restricted with computational power, so we can find out and filter out larger files and work with smaller ones.
2. Highly modifiable file size allows us to get lesser than or greater than any file size we want, which is a useful feature to keep in mind.

### Disadvantages
1. The type of the file isn't considered, nor are the contents. Without combination commands, this command is essentially put to sub optimal use.

### Example 1

```find skill-demo1-data -size -10M```

I wanted to find all the files below 10MB in size in our directory. This is the output. 

![Image](https://imgur.com/E4S7D01.png)

### Example 2

```find skill-demo1-data -size -1M```

I wanted the files below 1 MB in our directory. This is the output.

![Image](https://imgur.com/gBARSCk.png)





## Command 5- find and execute command

### format and usage

Suppose we want to find some file and then execute something on those files only. We use a combination ```find```.

```find <directory path/keyword> <criteria> <criteria input> -exec <command to be executed> {} \;```

```<criteria>``` could be ```-size```, or ```-type```, etc.
```<criteria input>``` is the input parameter that matches our filtering criteria
```-exec``` can chain and execute commands such as ```cat``` or ```ls```
```command``` here can be any command as per wish
```{}``` is essential for recursive application of ```-exec``` to the path returned by ```find```
```\;``` is the execution argument instantiator, i.e. without this our arguments are not instantiated and the command won't work


How this works is, ```find``` gets us the path we want to our files, ```-exec``` executes the commands we want recursively on that path.



### Advantages
1. This is the most useful command in the list and a combination command for ```find```. ```exec``` makes it easier to filter out and execute a set of instructions on only the files we want. 

### Disadvantages
1. We do not know the file contents.

### Example 1
Suppose we want to delete find-results.txt
We find this file and delete it by using 

```find skill-demo1-data  -name "find-results.txt" -exec rm {} \;```

Nothing was returned when I ran

```find skill-demo1-data  -name "find-results.txt"```

which means that it is confirmed this command erases the file.

![Image](https://i.imgur.com/w1a6D3s.png)

### Example 2

Suppose I want to display the contents of the file named "WhatToLasVegas.txt" in the "skill-demo1-data" directory.

I simply use 

```find skill-demo1-data -name "WhatToLasVegas.txt" -exec cat {} \;```

Which first finds the path of the file returned by the ```find``` command and then executes the ```cat``` command on all files in that path. The output is this.


![Image](https://imgur.com/6hNjQ6Q)
