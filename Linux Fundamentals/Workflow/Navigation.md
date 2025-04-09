We first login with the given credentials to access the excercise.

![Image](https://github.com/user-attachments/assets/02391ec0-f983-4afa-aa20-612baa24a3d7)

**Q) What is the name of the hidden "history" file in the htb-user's home directory?**

We use the *pwd* command to check whether we are in the correct directory. We then use the *ls -al* command to list all files in the directory including hidden ones.

```bash
pwd
ls
ls -al
```

![Image](https://github.com/user-attachments/assets/8d32fa77-9455-4691-b8cb-b4a12a477b7f)

From the picture we see that *.bash_history* is the answer.

**Q) What is the index number of the "sudoers" file in the "/etc" directory?**

We change our directory to *etc* by using the *cd /etc* command. 

```bash
cd /etc
ls -i | grep "sudoers"
```
![Image](https://github.com/user-attachments/assets/04197fb8-6036-4d79-8569-5876da00a094)

The *ls -i* is used to list the file name and their corresponding inode/index number. Since /etc contains a lot of files, I have used *grep* to only list files that have sudoers in their name, which gives us our answer.

**Answers:**
A) .bash_history
A) 147627