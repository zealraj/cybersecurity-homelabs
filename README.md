# cybersecurity-homelabs
home lab -1
Wᴇʙ Aᴘᴘ Aᴜᴛʜᴇɴᴛɪᴄᴀᴛɪᴏɴ(Oɴʟɪɴᴇ Pᴀꜱꜱᴡᴏʀᴅ Cʀᴀᴄᴋɪɴɢ ᴡɪᴛʜ Bᴜʀᴘ Sᴜɪᴛᴇ)



There are countless ways to hack web applications. As you know, a web application is an app that runs the website of everything from your neighbor's website to the all-powerful financial institution that runs the world. Each of these applications is vulnerable to attack, but not all are the same.



LAB:- We gonna find out how Burp Suite works to test  session ID randomization, injection attacks, fuzzing, and many other attacks.



Requirements :- Damn Vulnerable Web Application (DVWA) on our Metasploitable OS or the OWASP Broken Web App VM,Burp Suite.



Step 1:- Start by launching Kali and launching DVWA on another system or VM. Then start Burp Suite. First, the following screen will be displayed. In Community Edition, you can only create one "temporary project". Then click.Then select Use burp defaults and click Start Burp. Next, you need to click on the Proxy tab and enable the Intercept.



Step 2:- Then open your browser and set it to use a proxy. In Mozilla Firefox, go to Settings> Network Connections. There you will see a window like this: Set to forward browser requests on port xx on yy Be sure to click OK to have your browser save the new settings.



Step 3:-  Once the target system is up and running,  open a browser and go to the IP address of the Metasploittable system or the OWASP Broken WebApps VM. Go to DamnVulnerableWeb App (DVWA) on both systems. 

 When you get there, select DVWA and a login screen like the one below will open. 

 You have entered your OTW username and HackersArise password here. You do not have to enter the correct credentials.



Step 4: Before submitting your credentials, ensure that Burp Suite Proxy Interception is enabled and that your browser has proxy settings set. Then when you send the request, the proxy intercepts the request as shown in the screenshot below. 

 Note that my username and password are on the last line of the login request. 



Step 5:-Next, you need to send this request to BurpSuite Intruder. Right-click on this screen and select "Send to Intruder" as shown below. This will open the BurpSuite Intruder. On the first screen, the intruder displays the target's IP address. We have collected this information from intercepted requests. If you make a mistake, change it here. Also, note that we are assuming that you are using port 80. Again, if you're trying to authenticate on a different port or service, change it here. However, Burp Suite usually authenticates correctly. Then click the Position tab. The fields that you think.



Step 6:- Next, you need to set the attack type. BurpSuite Intruder has four types of attacks: 

1. Sniper A single set of 

 payloads. It targets any payload and places any payload in any position. 

2nd Cluster Bomb 

 Multiple payload sets. There is a different payload set for each location. 444 43rd pitchfork 

 Multiple payload sets. There is a different payload set for each location. Run each user data record at the same time. 

4 Battering ram A single set of 

 payloads. Takes a single payload set and executes it at each location. 

 See the Burp Suite documentation for more information on the differences between these payloads. The default for the 

 BurpSuite Intruder is Sniper, so leave it as Sniper for this attack. 

 Step 6: Set the  

 Payload Next, you need to set the 

 the payload that you have set. These are the squares that the intruder attacks. Select Payload Set # 1 and enter a common password found on almost every system, such as "admin", "guest", "system admin", "sys", "root", "password".Next, you need to configure the 

 payload that you have configured. These are the squares that the intruder attacks. Select Payload Set # 1 and enter a common password found on almost all systems, such as "admin", "guest", "systemadmin", "sys", "root", "password". 

 This will launch Burp Suite and try logging. Look up each password in the list to access DVWA. Notice in the screenshot above that both the status (302) and the length (558) are the same for each attempt. What we are looking for is a unique attempt at status and length, which indicates a successful login.



Step7:-In this technique, we can expect that each username or password is unknown to us. We will want to apply payloads; one the username, and one the password. We will Add each username subject and the password subject as payloads. We can even set the assault kind to "Cluster Bomb". 

 With this kind of assault, BurpSuite will attempt numerous mixtures of your listing in each username and password subject. This is an extra complicated and time-eating assault, however necessary, in case you don`t recognize the username. 

 Next, let's click on the Payloads tab. Select Payload set 2 and from the Payload kind pulldown window, pick Character Substitution. 

 With Character Substitution selected, BurpSuite will "munge" your password listing, changing ordinary letter/wide variety substitutions (customers are taught to extrude letters into numbers to save you dictionary attacks). As you could see below, the default person substitution is; 

 a=four b=8, e=three and so on. This is the everyday substitution that customers hire and need for paintings in maximum cases, however, you could personalize or upload different letter substitutions here.

Now, upload your password listing much like the preceding assault via way of means of clicking on the Load button to the left of the Items window. Note that rather than simply 10,000 requests as withinside the preceding attempt, now our tries have grown to over 2 billion! This is due to the fact every phrase can be tried as a username after which every phrase can be tried as a password. In addition, this approach will create extra passwords and usernames via way of means of the usage of the person substitution we enabled above. 

 In the very last step, click on "Start Attack". Since we can be trying 2 billion username and password mixtures, this could be a tedious and time-eating task. Here is in which the unthrottled BurpSuite Pro proves its value! 

 As you could see above, BurpSuite tries every phrase in our listing as a username after which attempts each phrase in our listing as a password. 

 Like withinside the assault above, we're searching out anomalies withinside the repute and period fields. These will frequently imply a Successful Login. 

 



Step:-8 Here it is essential to notice some things. First, is the repute column. Note that every one of the requests withinside the screenshot are "302" or "found". Also, notice that the period of the responses is all uniform (558). 

 That uniform period message will be the uniform terrible request reaction. When a reaction is of a distinctive period and a distinctive code (200), it'll warrant in the additional investigation, as it's far possible to have the appropriate username and password. You can locate those anomalies via way of means of clicking on the Status header or the Length header and kind the effects via way of means of those fields, in preference to manually looking through all 2 billion responses.
