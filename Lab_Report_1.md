**Lab Report 1, Julian Curatolo**

1.
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$ 
```
* pwd: /home/lecture1
* There was no argument provided for cd, which changes the working directory. With no path provided cd defaults to changing the pwd to the home directory. 
* no error

```
[user@sahara ~]$ ls
lecture1
```
* pwd: /home
* ls provides the files in the directory. This is lecture 1 for pwd: /home.
* no error

```
[user@sahara ~]$ cat
hello world!
hello world!
^C
```
* pwd: /home 
* No output and can use CtrlC to exit. cat with no argument allows the user to type into the terminal. Pressing enter after typing cat reads the line and prints it out on the next line. cat displays the contents of the files provided, without a file provided it can read contents typed into the terminal and then redisplay it. 
* No error

2.
```
[user@sahara ~]$ cd /home/lecture1/messages
```
* pwd: /home
* No output but changed the working directory to pwd:/home/lecture1/
* no error.

```
[user@sahara ~/lecture1]$ ls /home/lecture1/messages
en-us.txt  es-mx.txt  id.txt  zh-cn.txt
```
* pwd:/home/lecture1
* ls with a directory lists all the files in the directory.
* no error

```
[user@sahara ~/lecture1]$ cat /home/lecture1/
cat: /home/lecture1/: Is a directory
```
* pwd:/home/lecture1
* cat writes the contents of a file. A directory is not a file
* Error. Expected the contents but was not provided. 

3.
```
[user@sahara ~]$ cd /home/lecture1/messages/zh-cn.txt
bash: cd: /home/lecture1/messages/zh-cn.txt: Not a directory
```
* pwd:/home
* cd sets the pwd to a directory. The path to a file is not a directory
* Error. Expected to set the pwd to a file path but this could not be done.
``` 
[user@sahara ~]$ ls /home/lecture1/messages/zh-cn.txt
/home/lecture1/messages/zh-cn.txt
```
* pwd:/home
* Produced the path to the file. This output is different from when a path to a directory is given. A path to a directory prints the other directories or files within in that directory. Because zh-cn.txt has no files or directories within it, ls returns the path to the file.  
* no error.
```
[user@sahara ~]$ cat /home/lecture1/messages/zh-cn.txt
你好世界
```
* pwd:\home
* read the text within a file which is expected for cat.
* no error
