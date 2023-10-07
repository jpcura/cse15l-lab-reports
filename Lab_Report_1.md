##Lab Report 1, Julian Curatolo
1.
```
[user@sahara ~]$ cd
```
* pwd: /home
* There was no argument provided for cd, which changes the working directory, so no output or change in the directory occurred.
* no error

```
[user@sahara ~]$ ls
lecture1
```
* pwd: /home
* ls provides the files in the directory. This is lecture 1 for pwd: /home.
* no error

```
[user@saha ~]$ cat
```
* pwd: /home 
* No output and used CtrlC to exit. cat displays the contents of the directory provided
* error. No output was produced and I had to exit manually.
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
*pwd:/home/lecture1
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
*pwd:/home
* cd sets the pwd to a directory. The path to a file is not a directory
* Error. Expected to set the pwd to a file path but this could not be done.
``` 
[user@sahara ~]$ ls /home/lecture1/messages/zh-cn.txt
/home/lecture1/messages/zh-cn.txt
```
*pwd:/home
*Produced the path to the file. Without any directory contained within the file this makes sense. 
* no error.
```
[user@sahara ~]$ cat /home/lecture1/messages/zh-cn.txt
你好世界
```
* pwd:\home
* read the text with in a file wich is expected for cat.
* no error
