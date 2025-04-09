We first login with the given credentials to access the excercise.


![Image](https://github.com/user-attachments/assets/ca4692d9-db75-4f1e-b892-836c0ccff32f)

**Q) Find out the machine hardware name and submit it as the answer**

*uname* will provide basic information about the operating system name and system hardware.

```bash
uname --help
uname -i
```

By digging further into the command using the *--help* flag, we can see that we need to use the *-i* flag. Using the flag gives the answer the our 1st question.

![Image](https://github.com/user-attachments/assets/c98953f0-f08f-4b42-9b6c-ee8592bce52c)


**Q) What is the path to htb-student's home directory?**
Using the *pwd* gives the path to htb-student's home directory.

```bash
pwd
```

![Image](https://github.com/user-attachments/assets/db8df2cb-cd9d-41fb-bdba-08c8fd42fb3f)

**Q) What is the path to the htb-student's mail?**
Echoing the *$MAIL* environmental variable gives the answer.

```bash
echo $MAIL
```

![Image](https://github.com/user-attachments/assets/4681c48a-c9f5-4b95-afb0-d9f870a6b72b)


**Q) Which shell is specified for the htb-student user?**
Echoing the *$SHELL* environmental variable gives the answer.

```bash
echo $SHELL
```

![Image](https://github.com/user-attachments/assets/55a299ac-73bf-44d0-b52b-9b48a72f5e7c)

**Q) Which kernel release is installed on the system? (Format: 1.22.3)**
Looking back at the *uname --help* command, we see that we need to use the *-r* flag.

```bash
uname -r
```

![Image](https://github.com/user-attachments/assets/574a8693-4e63-4dfd-8dd9-03b0ccb33b64)

**Q) What is the name of the network interface that MTU is set to 1500?**

Using the *ifconfig* to list the network interfaces for the system, we see that only one has an MTU of 1500.

```bash
ifconfig
```

![Image](https://github.com/user-attachments/assets/27895ef5-b4a7-4d2b-8db0-32e1e02d601c)


**Answers:** <br>
A) x86_64 <br>
A) /home/htb-student <br>
A) /var/mail/htb-student<br>
A) /bin/bash<br>
A) 4.15.0<br>
A) ens192<br>