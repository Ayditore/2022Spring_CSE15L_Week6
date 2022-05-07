# Welcome to Anthony's Lab Report

In this report, I would like to show you how I manged to complete three tasks in lab 5.  

## Streamlining ssh Configuration  

* Firstly, find the **.ssh** folder on local computer. 

![1.1]()

* In the folder, the file called **id_rsa.pub** exists. It is a file which I used to store my passward on this computer tp login the server without typing the passward  

* Now, to make the login process even more quicker. I create a **txt** file called **config.txt**, and I type the following text into the txt file:

```
Host ieng6
    HostName ieng6.ucsd.edu
    User cs15lsp22ang (This is my username)
```  

![1.2]()

* Then, save the file and delete the **.txt** extension

![1.3]()

* Now, open a terminal and only type in **ssh ieng6**. As shown in the following screenshot, I do not even need to type in username to login to the server.  
* The login process is now faster! 

![1.4]()

