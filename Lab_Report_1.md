1.
```
[user@sahara ~]$ cd
```
* pwd: /home
* There was no argument provided for cd, which changes the working directory, so no output or change in directory occured.
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
* error. No output produced and had to manually exit.
2.
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$ cd /home/lecture1/
```
* pwd: /home
* No output but changed the working directory to pwd:/home/lecture1/
* no error.

```
[user@sahara ~/lecture1]$ ls /home/lecture1/
Hello.class  Hello.java  messages  README
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
[user@sahara ~]$ ls /home/lecture1/messages/zh-cn.txt
/home/lecture1/messages/zh-cn.txt
[user@sahara ~]$ cat /home/lecture1/messages/zh-cn.txt
你好世界
```
