**Q) Which TCP port is open on the remote host?**

I ran nmap to identify open tcp ports.

8080 is the only tcp port open.

![Image](https://github.com/user-attachments/assets/7f4de9f7-e3eb-48e3-a509-81d624a23bcf)

**Q) Which web server is running on the remote host? Looking for two words.**

From the previous picture we see that it runs on Apache Tomcat.

**Q) Which relative path on the webserver leads to the Web Application Manager?**

Running the IP on port 8080 in the web browser gives the following.

![Image](https://github.com/user-attachments/assets/9c92b1e4-9d1b-4be9-bebb-663aaa8e948c)

Clicking on the Manager App, I get the following webpage.

![Image](https://github.com/user-attachments/assets/20ac9f11-7a65-4929-a22e-94df0a5ee3fe)

Looking at the URL gives the answer.

**Q) What is the valid username and password combination for authenticating into the Tomcat Web Application Manager? Give the answer in the format of username:password**

Since I don't have any credentials to work with, I searched *tomcat default credentials* that ultimately directed me to https://github.com/netbiosX/Default-Credentials/blob/master/Apache-Tomcat-Default-Passwords.mdown.

I created 2 files, *username.txt and password.txt* using the terminal.
![Image](https://github.com/user-attachments/assets/82ac9d06-d5dc-48a8-b62d-cd4a6c6312c8)

![Image](https://github.com/user-attachments/assets/cb7ff244-e386-4bf3-ac71-7576dd1cce3a)

I then used Metasploit to brute force the credentials.

![Image](https://github.com/user-attachments/assets/ded6db70-5be1-439c-8502-1efee98d66bb)

Typign *search tomcat* gives the following.

![Image](https://github.com/user-attachments/assets/854a18f6-5c00-47cc-acd2-c58e0bcf5337)

I selected module 64 by using *use 64* command. I then used show options to see the arguments to be set. 

![Image](https://github.com/user-attachments/assets/5ad42fd9-35f0-4f74-b444-7f3e31658447)
![Image](https://github.com/user-attachments/assets/42053a03-ab28-4aa6-83c7-2731dbc1905a)

I get a set of valid credentials, *tomcat:s3cret*.


Using the credentials I am able to login to the application through the Tomcat Web Application Manager. 

![Image](https://github.com/user-attachments/assets/6228f9c6-d46a-4d7b-8ac5-a0cbd3712bfb)

**Q) Which file type can be uploaded and deployed on the server using the Tomcat Web Application Manager?**


Scrolling down, I see that *war* is the only file that can be deployed.

![Image](https://github.com/user-attachments/assets/46f6af23-443f-4a3e-809d-44f0085c00a5)

**Q) Submit the flag located on the user's desktop.**

Using the same picture as before, I used module 18.

![Image](https://github.com/user-attachments/assets/854a18f6-5c00-47cc-acd2-c58e0bcf5337)

![Image](https://github.com/user-attachments/assets/b34b1a60-6977-4bc9-902a-7f0f4460a19a)

I then set the relevant options.

![Image](https://github.com/user-attachments/assets/f8d533b3-b69f-4971-a532-8ed26106209a)

Using *getuid*, I can confirm that I have a shell on the application.

Navigating to *C:\Users\Administrator\Desktop\flags* using *cd*, we get both the flags.
![Image](https://github.com/user-attachments/assets/aaefeafd-555c-49ad-b8f3-13068e713b02)

**Q) Submit the flag located on the administrator's desktop.**
Navigating to *C:\Users\Administrator\Desktop\flags* using *cd*, we get both the flags.

![Image](https://github.com/user-attachments/assets/aaefeafd-555c-49ad-b8f3-13068e713b02)


**Answers:**
<br> A) 8080 
<br> A) Apache Tomcat
<br> A) /manager/html
<br> A) tomcat:s3cret
<br> A) war
<br> A) 7004dbcef0f854e0fb401875f26ebd00
<br> A) 04a8b36e1545a455393d067e772fe90e