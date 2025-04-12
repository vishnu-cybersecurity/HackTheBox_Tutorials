We first login with the given credentials to access the excercise.

![Image](https://github.com/user-attachments/assets/9207c20f-9cb4-47c5-b07c-ab1a8f8916d7)


**Q) How many files exist on the system that have the ".log" file extension?**


I used the *find* command with several flags to get the answer.

```bash
find / -type f -name *.log 2> /dev/null | wc -l
```

- */* tells the *find* command to start search from root directory
- *-type f* tells the find command to only search for files
- *-name \*.loh* tells the file command search for all files that end with *.conf* extension
- *2> /dev/null* sends all errors and *Permission Denied* requests to a null directory. This command displays all successful requests.
- *|* is used to direct the output of the left command into the input of the right command
- *wc -l* is used to count the number of line of output from the previous command

**Q) How many total packages are installed on the target system?**

Taking help from https://www.baeldung.com/linux/list-installed-packages we use the following command to get our answer.

```bash
dpkg --get-selections | grep -w "install" | wc -l
```
- *––get-selections* returns a list of package selections and writes the output to stdout. 
- *grep -w "install"* selects the lines that match the word "install" as a whole word
- *|* is used to direct the output of the left command into the input of the right command
- *wc -l* is used to count the number of line of output from the previous command

![Image](https://github.com/user-attachments/assets/3660426b-c68f-4df1-82a0-aea7a1fbdaaa)




**Answers:** <br>
A) 32 <br>
A) 737