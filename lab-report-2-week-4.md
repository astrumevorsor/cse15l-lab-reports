# Part 1- Setting up the StringServer
I have used chatGPT to generate the StringServer code using the NumberServer and Server.java methods provided to us from github. 

These are the prompts I used. 

```Let us suppose I have 2 files with the following code: 

NumberServer.java 

import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Number: %d", num);
        } else if (url.getPath().equals("/increment")) {
            num += 1;
            return String.format("Number incremented!");
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("count")) {
                    num += Integer.parseInt(parameters[1]);
                    return String.format("Number increased by %s! It's now %d", parameters[1], num);
                }
            }
            return "404 Not Found!";
        }
    }
}

class NumberServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

and Server.java

// A simple web server using Java's built-in HttpServer

// Examples from https://dzone.com/articles/simple-http-server-in-java were useful references

import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.URI;

import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

interface URLHandler {
    String handleRequest(URI url);
}

class ServerHttpHandler implements HttpHandler {
    URLHandler handler;
    ServerHttpHandler(URLHandler handler) {
      this.handler = handler;
    }
    public void handle(final HttpExchange exchange) throws IOException {
        // form return body after being handled by program
        try {
            String ret = handler.handleRequest(exchange.getRequestURI());
            // form the return string and write it on the browser
            exchange.sendResponseHeaders(200, ret.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(ret.getBytes());
            os.close();
        } catch(Exception e) {
            String response = e.toString();
            exchange.sendResponseHeaders(500, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        }
    }
}

public class Server {
    public static void start(int port, URLHandler handler) throws IOException {
        HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);

        //create request entrypoint
        server.createContext("/", new ServerHttpHandler(handler));

        //start the server
        server.start();
        System.out.println("Server Started! Visit http://localhost:" + port + " to visit.");
    }
}
Can you give me a line by line explanation of the code
```

ChatGPT gave a response

```Sure! Here's a line by line explanation of the code:

NumberServer.java

import java.io.IOException;: Importing the IOException class from the java.io package.
import java.net.URI;: Importing the URI class from the java.net package.
class Handler implements URLHandler: A class named Handler that implements an interface named URLHandler.
int num = 0;: Declaring an instance variable num and initializing it with 0. This variable holds the number that the server manipulates.
public String handleRequest(URI url): A method named handleRequest that takes a URI object as a parameter and returns a string.
if (url.getPath().equals("/")): If the path component of the URI is equal to /, return a string with the value of num.
else if (url.getPath().equals("/increment")): If the path component of the URI is equal to /increment, increment num by 1 and return a string indicating that the number was incremented.
else: If the if and else if conditions aren't satisfied,
System.out.println("Path: " + url.getPath());: Print the path component of the URI.
if (url.getPath().contains("/add")): If the path component contains /add,
String[] parameters = url.getQuery().split("=");: Split the query component of the URI by = and store the result in an array of strings named parameters.
if (parameters[0].equals("count")): If the first element of parameters is equal to "count",
num += Integer.parseInt(parameters[1]);: Increase the value of num by the integer representation of the second element of parameters.
return String.format("Number increased by %s! It's now %d", parameters[1], num);: Return a string indicating that the number was increased by the second element of parameters and the current value of num.
return "404 Not Found!";: Return the string "404 Not Found!" if none of the conditions are satisfied.
class NumberServer: A class named NumberServer with a main method.
public static void main(String[] args) throws IOException: The main method of the NumberServer class, which takes an array of strings named args as a parameter and throws an IOException.
if(args.length == 0): If args has a length of 0,
System.out.println("Missing port number! Try any number between 1024 to 49151");: Print a message indicating that the port number is missing and that the user should try a number between 1024 to 49151.
return;: Return from the main method.
int port = Integer.parseInt(args[0]);: Store the integer

Here's an explanation for the code in Server.java:

The code starts with importing the required Java libraries:
import java.io.IOException;: Exception for input/output operations in Java.
import java.net.InetSocketAddress;: A class that represents an IP address and a port number.
import java.net.URI;: A class to represent a URI (Uniform Resource Identifier) in Java.
import com.sun.net.httpserver.HttpExchange;: Class in the Java library to represent a single HTTP request-response transaction.
import com.sun.net.httpserver.HttpHandler;: A interface in the Java library that handles a single HTTP request.
import com.sun.net.httpserver.HttpServer;: Class in the Java library that implements an HTTP server.
The next definition is the URLHandler interface with a single method:
String handleRequest(URI url): The method takes a URI object as a parameter and returns a string. The method definition is not implemented in this class, it is implemented by the implementing class.
The next class is ServerHttpHandler that implements the HttpHandler interface. This class is used to handle a single HTTP request and return an HTTP response. The class constructor takes a URLHandler object as a parameter.
The handle() method is overridden to form the response body by calling the handleRequest() method of the URLHandler object. It forms the return string and writes it to the browser. If an exception occurs, the response is set to a 500 status code.
Finally, the Server class has the start() method that starts the server by creating an instance of HttpServer. It creates a context for the "/" endpoint and passes the ServerHttpHandler object to it. The server is then started and a message is printed to the console indicating that the server has started.
I hope this helps! Let me know if you have any other questions.
```
I understood the methods and decided to copy the code from Server.java without any modifications as it's job was to set up the Server and serve as an interface for StringServer.java, as it did not have a main method.

StringServer would need a main to run the code and I'd have to change int to string, the function handleRequest would have to be modified to accomodate and display the string messages from the prompt. 

So, what I did to the code was, simply changed it to, 
```import java.io.IOException;
import java.net.URI;

//Declare class stringserver and use the String type object as we learnt in CSE 11.
//Here the String objects cannot be used as we want a modifiable string in our website
class StringHandler implements URLHandler {
    //initialise as a non-null string object
    String message = new String();
```

and 

```
lass StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);
        Server.start(port, new StringHandler());
    }
}
```
I had confusions with handleRequest, I had written the below code but was clueless to go about it next. I used chatGPT to generate the message code. 

```
public String handleRequest(URI url) {
        System.out.println(url.getPath());
        //similar to the add method from number server
        if (url.getPath().contains("/add-message")) {
        /**
        insert code for message here
        */
        //no valid args.
        return "404 Not Found!";
```


My prompt:

```
how do i change this code to accept string and create a web server called StringServer that supports the path and behavior described below. It should keep track of a single string that gets added to by incoming requests. The requests should look like this:

/add-message?s=<string>
The effect of this request is to concatenate a new line (\n) and the string after = to the running string, and then respond with the entire string so far.
```

ChatGPT response (confirming my stringserver implementation was accurate)

```
import java.io.IOException;
import java.net.URI;

class StringHandler implements URLHandler {
    String str = "";

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                str += "\n" + parameters[1];
                return str;
            }
        }
        return "404 Not Found!";
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);
        Server.start(port, new StringHandler());
    }
}
```
I took the middle part and asked chat gpt to explain this section of code.

My response: explain ```  if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                str += "\n" + parameters[1];
                return str;
            }
        }
        ```
ChatGPT: ```This code implements the StringServer class which is a simple web server that allows incoming requests to modify a single string by concatenating a new line (\n) and the string after the equal sign (=) in the query parameter s. The web server listens on a specified port, which should be passed as the first argument when starting the server.

The StringHandler class implements the URLHandler interface and defines the behavior for handling incoming requests. It has a single instance variable str which is initially an empty string. The handleRequest method is called by the ServerHttpHandler to handle incoming requests and returns the current string after modifying it.```

So, I followed this method and added this to the code. 


This was the final result. 

![Image](https://i.imgur.com/3dDIbXH.png)

![Image](https://i.imgur.com/cEJEEdj.png)

![Image](https://i.imgur.com/9RF0Luq.png)

For each of the two screenshots, describe:

## Which methods in your code are called? What are the relevant arguments to those methods, and the values of any relevant fields of the class?
We call the ```StringHandler``` object which calls the handleRequest method. This requests to modify our string message in the URI link and update and display the message on the output stream. 

as for server.java, basically serves as the backend interface of our server with how to implement what we want to display using the StringServer. 

  


## How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
No fields change as no updating to the instance variables. The value of string message gets updated however it is a non-instance variable. 


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




