We first login with the given credentials to access the excercise.

![Image](https://github.com/user-attachments/assets/4b2dfb93-288e-4738-999c-07fb335d4ac0)


**Q) What is the name of the last modified file in the "/var/backups" directory?** 

We first navigate to the required directory using the *pwd command*. Taking help from https://linuxcommandlibrary.com/man/ls , we can understand the flags to be used.

The *-l* is used to list the files and *-t* is used to sort based on time the file was modified. The first file will indicate the last modified file.

```bash
cd /var/backups
ls -lt
```

![Image](https://github.com/user-attachments/assets/1b9badb4-fbf5-4c20-a279-b83305f26940)


**Q)What is the inode number of the "shadow.bak" file in the "/var/backups" directory?**

We can use the *-i* flag to get the index/inode number in conjuction with the *grep* command to get the specific file.

```bash
ls -i | grep shadow.bak
```

![Image](https://github.com/user-attachments/assets/2f34fa45-500f-4e03-8c93-b22c06057ab6)

**Answers:** <br>
A) apt.extended_states.0 <br>
A) 265293