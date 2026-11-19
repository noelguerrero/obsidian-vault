
#### Use `.` on the first part of the name of the file to hide it.

**Without** `.` 

Note: I use `ls -l` to show the directories/folder
![[Pasted image 20261119212342.png]]

**With **`.` 

Note: I use `ls -la` to show the normal and also the hidden directories/folder
![[Pasted image 20261119212500.png]]


****
### Accessing configuration file requires a specific user level

Linux have **user-application configuration file** that configure the bahavior of the application. Also it have **server-wide configuration file** that configure the behavior of the whole linux kernel. 

Basic User level is enough to access the configuration file of the user applications, but the server-wide configuration file like `etc` and other requires superuser or root priviledges.

****