# Part 1- Setting up the StringServer

![Image](https://i.imgur.com/YVG1Ufy.png)

![Image](https://i.imgur.com/wzyEidJ.png)

For each of the two screenshots, describe:

## Which methods in your code are called? What are the relevant arguments to those methods, and the values of any relevant fields of the class?
The only method locally defined is @handle which takes in an HttpExchange type object, returns void and throws an IOexception for a possible error if there are any. 

As for methods, I use ```HttpServer.create(<socket address object>)``` to assign a value to the Http Server.
We use instance methods ```.createContext()```, which handles incoming requests to the prompt specified add message path. If you don't add context, it throws 404 not found. 
We use ```.setExecutor()``` and set the server default to null.
We use ```.start()``` to start the server.

In the AddMessageHandler class we use ```.getRequestURI()``` which is used to get the value of URI request.
```.getQuery()``` gets the query part of the http link.
The later part of the code appends the message in byte format to the webpage.

```os``` is the output stream which gets the response body, writes it and displays it, then closes it. 
  


## How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

```   
      String message = query.substring(query.indexOf("=") + 1);
      messageBuilder.append(message).append("\n");
      byte[] response = messageBuilder.toString().getBytes();
      obj.sendResponseHeaders(200, response.length);
```
No fields change in this code. 
The message field is static, meaning it belongs to the class rather than instance variables, and is shared across all instances. 
Its value is updated with each incoming request and is returned as the response to the client.

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
      int[] input1 = {1,2,2,1};
      assertArrayEquals(new int[]{1,2,2,1}, ArrayExamples.reversed(input1));
    }
 ```
This is a pallindromic input which gives an accurately OK test.

Symptom ![Image](https://i.imgur.com/6VqoC4Q.png)




Buggy code 
![Image](https://i.imgur.com/qlU5Twi.png)


Corrected code

![Image](https://i.imgur.com/AqFAioN.png)






