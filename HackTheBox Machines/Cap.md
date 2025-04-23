**Q) How many TCP ports are open?**

We use _nmap_ to identify open tcp ports.

```bash
nmap -sV 10.129.234.187 | tee data.txt
```

![Image](https://github.com/user-attachments/assets/fb39435e-9ffd-4f7c-9b6d-e0c01139f55b)

* The _-sV_ flag is used for service version detection
* *tee* command is used to display the output to the terminal and write to the data.txt file

We can see 3 ports open which is our answer.

We will now open the IP in the web browser. We get the following web browser.

![Image](https://github.com/user-attachments/assets/41b3d1a5-bee5-46e4-a03c-d609c557b514)

**Q) After running a "Security Snapshot", the browser is redirected to a path of the format /[something]/[id], where [id] represents the id number of the scan. What is the [something]?**

After clicking on the Security Snapshot tab we get the following.

![Image](https://github.com/user-attachments/assets/feb152b5-03b2-41dc-9470-65ceec83d7a5)

We see our answer in the URL, data, which is our answer.

**Q) Are you able to get to other users' scans?**

We have *1* after data in the URL. We can download the file. I will change the *1* to *0*. This displays another page where we can download another file. Seeing the downloads we can confirm that these are 2 different files and hence access other users' scans. However we can only access users 0 and 1. 

![Image](https://github.com/user-attachments/assets/bb37c5b1-19ae-4404-9e1a-09fdb70c5631)


**Q) What is the ID of the PCAP file that contains sensative data?**

Opening 0.pcap, we get the following picture.

![Image](https://github.com/user-attachments/assets/8e1e15a0-c759-4296-ad2c-c7b83d9e5308)

Scrolling through the files gives is crucial information.

**Q) Which application layer protocol in the pcap file can the sensative data be found in?**

We can look at **No.36**. We see that sensative data is found in the *ftp* protocol.  

![Image](https://github.com/user-attachments/assets/d94ff411-2234-440c-ac02-074cb4552431)

**Q) We've managed to collect nathan's FTP password. On what other service does this password work?**

We know from the first picture that ports 21,22 and 80 are open. 21 is ftp, 22 is ssh and 80 is http.

We try the gathered credentials on the ftp and ssh ports.

![Image](https://github.com/user-attachments/assets/09b34014-0650-4373-8e5b-24c597e508ea)

It works on ftp port.

![Image](https://github.com/user-attachments/assets/9fb8f673-fdb7-47c4-be89-96bd2d04e453)

It works on ssh port.


**Q) Submit the flag located in the nathan user's home directory.** 

After logging in I look the file contents using *ls*. I then view the file using *cat* to get the answer.

![Image](https://github.com/user-attachments/assets/ee8a536a-d54a-4919-9e8f-41bc75c23437)

**Q) What is the full path to the binary on this machine has special capabilities that can be abused to obtain root privileges?**

Taking help from the hints provided, I download the linpeas.sh from the following repo using curl, https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS.  


I open a new terminal and use the curl command.

```bash
curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh | sh
```

![Image](https://github.com/user-attachments/assets/ba4ec3e9-c9f1-4b65-862a-06c2a68f41cd)



**Q) Submit the flag located in root's home directory.**


Answers: <br>
A) 3 <br>
A) data
<br> A) yes
<br> A) ftp
<br> A) ssh
<br> A)
<br> A) 