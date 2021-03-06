# Welcome to Anthony's Lab Report

In this report, I would like to show you how I manged to complete three tasks in lab 5.  

## Streamlining ssh Configuration  

* Firstly, find the **.ssh** folder on local computer. 

![1.1](1.1-ssh_folder.png)

* In the folder, the file called **id_rsa.pub** exists. It is a file which I used to store my passward on this computer tp login the server without typing the passward  

* Now, to make the login process even more quicker. I create a **txt** file called **config.txt**, and I type the following text into the txt file:

```
Host ieng6
    HostName ieng6.ucsd.edu
    User cs15lsp22ang (This is my username)
```  

![1.2](1.2-create_config.png)

* Then, save the file and delete the **.txt** extension

![1.3](1.3-delete_extension.png)

* Now, open a terminal and only type in **ssh ieng6**. As shown in the following screenshot, I do not even need to type in username to login to the server.  
* The login process is now faster! 

![1.4](1.4-login.png)

* Then, I used the 'scp' command as `scp [file name] ieng6:~/` to copy a file from local computer to the server.

![1.5](1.5-scp.png)

* After login, we can see that the file is successfully updated.

![1.6](1.6-scp_result.png)

---
## Setup Github Access from ieng6

* First, I cloned my markdown-parser repo onto the ieng6 server

![2.1](2.1-clone.png)

* From the picture, we can see that when `push` the file to the Github after making change, an error occurs after password authentication to access Github.

![2.2](2.2-push_error_message.png)

* To solve this issue, I generated a new public key in server by using the code of `ssh-keygen -t rsa -C "[github email]"`:

![2.3](2.3-gen_key.png)

* The newly generated key is saved in the server `.ssh` file

![2.3b](2.3b-save_key.png)

* After generating the keys, I use `cat` to get public key from **id_rsa.pub** located in **.ssh** folder, and copy it to the *SSH key* in Github setting.

![2.4](2.4-cat.png)

* Github Setting Page:

![2.5](2.5-github_ssh.png)

* Then I use Github SSH key clone, which is `git@github.com:Ayditore/markdown-parser.git` to clone *markdown-parser* to the *ieng6* server.

![2.6](2.7-ssh_clone.png)

* After clone, I go into the *markdown-parser* directory and use `touch` to add a new blank text file called "hello.txt"

![2.8](2.8-ssh_touch.png)

* Then I use `git add . ` and `git commit -m "[commit description]"` to add and commit to the Github.

![2.9](2.9-ssh_add_file.png)

* Last, I used `git push` to push commit to Github. Then we are now able to see the file I added from Github webpage.

![2.10](2.10-ssh_push.png)
![2.10b](2.10b-ssh_push.png)

## Update
_**Link to the page where I commited "hello.txt" to the repo**_  
[Link to commit history](https://github.com/Ayditore/markdown-parser/commit/9d4511ea13138ddf79399a25c4237592c350fa1c)  

[**Link to repo with hello.txt**](https://github.com/Ayditore/markdown-parser)

---
## Copy whole directories with `scp -r`
* First, I copied a **markdown-parse** directory to the the server by using following code:

```
scp -r . cs15lsp22ams@ieng6.ucsd.edu:~/markdown-parse
```

![3.1](3.1_scp-r.png)

* After running `ls` comman, we can see the folder of **markdown-parse** and documents in the folder are in the server.

![3.2](3.2-all_file.png)

* Now run the JUnit test directly on the server by using the code:

```
cd markdown-parse; javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest
```

*The result is
![3.3](3.3-oneline.png)

* Then, to improve the efficiency of code, I combined `scp`, `;`, and `ssh` to copy the whole directory and run the tests in one line.

```
ssh ieng6 "scp -r . cs15lsp22ams@ieng6.ucsd.edu:~/markdown-parse; cd markdown-parse; javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"
```

* Then, after running this one line command, the same result will appear.

## Update
_**The last two pictures are updated based on feedback**_  
![3.4](3.4-oneline.png)
![3.4b](3.4b-oneline_result.png)