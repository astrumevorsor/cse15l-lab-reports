# Part 1- Setting up the StringServer



For each of the two screenshots, describe:

## Which methods in your code are called? What are the relevant arguments to those methods, and the values of any relevant fields of the class?
The only method locally defined is @handle which takes in an HttpExchange type object, returns void and throws an IOexception for a possible error if there are any. 


  


## How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.



# Part 2- Bugs and Symptoms

## Choose one of the bugs from lab 3
I will refer to the ```reversed() ``` method. 

```@Test 
public void testReversed(){
 int [] input= {1, 2, 3, 4, 5};
 assertArrayEquals(new int[] {5, 4, 3, 2, 1}, ArrayExamples.reversed(input));
```
It is observed that the first element of the array in the actual output does not match the expected output. It should have been 5, but is 0.

```@Test 
    public void testReversed() {
      int[] input1 = {0,0};
      assertArrayEquals(new int[]{0,0}, ArrayExamples.reversed(input1));
    }
 ```
This is a pallindromic zero input which gives an accurately OK test.

Symptom ![Image](https://i.imgur.com/6VqoC4Q.png)


Correct test: 

![Image](https://i.imgur.com/JcUEeyz.png)




Buggy code 
![Image](https://i.imgur.com/qlU5Twi.png)


Corrected code

![Image](https://i.imgur.com/AqFAioN.png)

## Part 3- Learning Outcomes

Through the lab, I learnt how to script my own webserver and the procedures behind requesting and sending data.
I also learnt that chatGPT generated code is incorrect and often must be modified to fit the requirements of the interface. 
I used to think everything is complicated but it turns out the web is a file system which can be broken into simpler parts and we can create our own webpages. 
This is very useful if I wish to create a website of my own or host a domain in the future.




