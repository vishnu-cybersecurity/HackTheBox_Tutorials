We first login with the given credentials to access the excercise.

![Image](https://github.com/user-attachments/assets/4b2dfb93-288e-4738-999c-07fb335d4ac0)

**Q)What is the name of the config file that has been created after 2020-03-03 and is smaller than 28k but larger than 25k?**

I used the *find* command with several flags to get the answer.

```bash
find / -type f -name *.conf -size +25k -size -28k 2> /dev/null
```

- */* tells the *find* command to start search from root directory
- *-type f* tells the find command to only search for files
- *-name \*.conf* tells the file command search for all files that end with *.conf* extension
- *-size +25k -size -28k* tells the find command to search for files that are larger than 25k but smaller than 28k.
- *2> /dev/null* sends all errors and *Permission Denied* requests to a null directory. This command displays all successful requests.

![Image](https://github.com/user-attachments/assets/9bb5befb-ef18-4c98-8479-a45102fe5125)

**How many files exist on the system that have the ".bak" extension?**

I used the *find* command with several flags to get the answer.

```bash
find / -type f -name *.bak 2> /dev/null
```
- */* tells the *find* command to start search from root directory
- *-type f* tells the find command to only search for files
- *-name \*.bak* tells the file command search for all files that end with *.bak* extension
- *2> /dev/null* sends all errors and *Permission Denied* requests to a null directory. This command displays all successful requests.

We can see that we have 4 files with *.bak extension*.

![Image](https://github.com/user-attachments/assets/437464dc-8c16-4e0d-b5b8-102c022f28d6)


**Answers:** <br>
A) 00-mesa-defaults.conf <br>
A) 4