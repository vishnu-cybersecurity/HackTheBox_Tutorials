**Q) How many TCP ports are open?**

I ran _nmap_ to identify open tcp ports.

```bash
nmap -sV 10.129.2.36 | tee data.txt
```

![Image](https://github.com/user-attachments/assets/fb39435e-9ffd-4f7c-9b6d-e0c01139f55b)

* The _-sV_ flag is used for service version detection
* *tee* command is used to display the output to the terminal and write to the data.txt file

I have written to the *data.txt* file so that I can look at the nmap scan results without needing to scroll to the result in the terminal.

I can see 3 ports open which is our answer.

I will now open the IP in the web browser. I get the following web browser.

![Image](https://github.com/user-attachments/assets/c949b935-6d42-4640-a143-0d80d655daa0))

**Q) After running a "Security Snapshot", the browser is redirected to a path of the format /[something]/[id], where [id] represents the id number of the scan. What is the [something]?**

After clicking on the Security Snapshot tab, I get the following.

![Image](https://github.com/user-attachments/assets/d4c88d41-a945-467d-ac55-85be0e2a0b6d)

I see our answer in the URL, *data*, which is the answer.

**Q) Are you able to get to other users' scans?**

The number *1* is displayed after *data* in the URL. I downloaded the file. I will change the *1* to *0*. This displays another page where I can download another file. Seeing the downloads I can confirm that these are 2 different files and hence access other users' scans. Noting that I can only access users 0 and 1. 

![Image](https://github.com/user-attachments/assets/1cd366ff-02c5-4748-87e9-de20d9722545)


**Q) What is the ID of the PCAP file that contains sensative data?**

Opening 0.pcap and 1.pcap with Wireshark, I get the following picture.

![Image](https://github.com/user-attachments/assets/ccbab88d-098b-4af8-83b0-9fd0d6ba2f4c)

![Image](https://github.com/user-attachments/assets/b8dfba77-aca0-47e0-a37e-ddb03faa0ca9)

I see that 1.pcap is empty.
Scrolling through 0.pcap gives us crucial information.

**Q) Which application layer protocol in the pcap file can the sensative data be found in?**

I look at **No.36** and **No.40**. I see that sensative data is found in the *ftp* protocol.  

![Image](https://github.com/user-attachments/assets/d4f06b14-d352-4b4f-bd8c-32911b849eba)

**Q) We've managed to collect nathan's FTP password. On what other service does this password work?**

I know from the first picture that ports 21,22 and 80 are open. 21 is ftp, 22 is ssh and 80 is http.

I try the gathered credentials on the ftp and ssh ports.

![Image](https://github.com/user-attachments/assets/9d7f9b2b-2877-4a38-9df3-46bd4f6d3b79)

It works on ftp port. I have copied the *user.txt* from nathan using ftp and then displaying the contents.

![Image](https://github.com/user-attachments/assets/0bb1b453-1cba-4b76-8267-6ef194d9b5fc)

It works on ssh port.


**Q) Submit the flag located in the nathan user's home directory.** 

![Image](https://github.com/user-attachments/assets/9d7f9b2b-2877-4a38-9df3-46bd4f6d3b79)

Taking reference from the previous steps, I have copied the *user.txt* from nathan using ftp and then displaying the contents of the file. This is the user flag. ***Note, each user has a different flag.***

**Q) What is the full path to the binary on this machine has special capabilities that can be abused to obtain root privileges?**

I opened a new terminal and created a new folder called linpeas. Taking help from the hints provided, I download the linpeas.sh from the following repo using wget, https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS. 


```bash
wget https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh
```

![Image](https://github.com/user-attachments/assets/ba4ec3e9-c9f1-4b65-862a-06c2a68f41cd)

I then start a web server on port 8080.

```bash
sudo python3 -m http.server 8080
```

![Image](https://github.com/user-attachments/assets/0751b6f9-46dc-4bb5-9c34-7aaa0ae3304a)

I then navigate back to the terminal with the ssh session. I fetch and then execute the linpeas file. This runs the linpeas.sh script in the ssh session on nathan's machine. 

![Image](https://github.com/user-attachments/assets/e7d1fce3-d07d-4f84-aa2f-5acbaea4ad78)

Using the hint given, I search for the *Files with capabilities*. I can see that */usr/bin/python3.8*, has cap_setuid privileges. Taking reference from https://www.elastic.co/docs/reference/security/prebuilt-rules/rules/linux/privilege_escalation_suspicious_uid_guid_elevation, any program having cap_setuid as the ability to run as root even as an unprivileged user. This is our answer to the question.

![Image](https://github.com/user-attachments/assets/2ec8dd0b-4d52-4372-a84b-d2ab3a6c1e2f)

**Q) Submit the flag located in root's home directory.**

I run python to get root privileges. The following python commands are used to get a root shell on the machine.

```bash
python3
import os
os.setuid(0)
os.system("/bin/bash")
id
ls
cd /root
cat root.txt
```
- Running the *id* command confirms I am root user while being in the same group as nathan.
- Running the *ls* command shows the contents of the directory.
- Running the *cd /root* command changes to *root* directory.
- Running the *cat* command displays the contents of *root.txt* which is our flag.

![Image](https://github.com/user-attachments/assets/18bcfecd-d743-44d2-8429-371f1afb1ece)

**Answers: <br>**
A) 3 <br>
A) data
<br> A) yes
<br> A) ftp
<br> A) ssh
<br> A) c60cbb44471f2d34a45ae669310afa06
<br> A) /usr/bin/python3.8
<br> A) 12686e0eaa5cf8d5c11fcaff70e54362