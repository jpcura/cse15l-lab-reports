**Lab Report 2**

**Part 1**
![image](https://github.com/jpcura/cse15l-lab-reports/assets/146609257/c5e5f42e-c3bf-42ca-948f-efeb4f6db464)
Which methods in your code are called?
* the handleRequest(URI url) method is called.  
* The argument given is the url (HTTP://localhost:4005/add-messages?s=Hello). The value of field String s = ""; at the start. The value of field Integer n = 0 at the start. Once the url passes the if statement the array String[] para gets created with objects {"s", "Hello"} since it splits at =.
* It checks that "s" is at index 0 and then updates field n one value (0 to 1). It updates field s to "\n1. Hello". It then returns s. The changes to s and n are constant throughout the time that the server is running. The changes to String[] para are only available with each method call since each time handle Request declares a new array. 

![image](https://github.com/jpcura/cse15l-lab-reports/assets/146609257/b5f3fb1b-ef89-47fc-b427-cef0efa1ac14)
*the method handleRequest(URI URL) method is called.
*the argument given is the url (HTTP://localhost:4005/add-messages?s=Today is Friday). The field Integer n = 1 at start. The field String s = "/n1. Hello"at the start. String[] para gets created with the objects {"s", "Today is Friday"}. 
* It checks that "s" is at index 0 and then updates field n to n = 2. It updates field s to "\n1. Hello\n2. Today is Friday". The changes to s and n will remain constant while the server is constant. The changes to String para[] will go away after the method is finished running.


**Part 2**
![image](https://github.com/jpcura/cse15l-lab-reports/assets/146609257/7154df26-e3a9-43e0-bf4a-e96a373d216a)
![image](https://github.com/jpcura/cse15l-lab-reports/assets/146609257/0a12acee-f3a3-4f49-b635-2e5be69e1780)
![image](https://github.com/jpcura/cse15l-lab-reports/assets/146609257/a828062c-8b9b-464c-9358-aaff399160df)

**Part 3**
I learned how to start a server using java and how making changes inside the server works. I also learned how to connect to a computer remotely and how to make changes to and see the files on that computer. 
