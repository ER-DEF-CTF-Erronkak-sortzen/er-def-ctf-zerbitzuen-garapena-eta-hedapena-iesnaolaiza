

# Service definition:
- We have two dockers: 
1. An Ubuntu (latest version) one which contains the flags. 
2. One who has install FTP service. 
The attacker has access to ftp (web_docker) with the default password 'anonymous' and has to look for information that can help him accessing the other docker.
The flags are stored in that last docker's file and attacker has to let them in his T-Submission machine. 
 
# Service implementation:
FTP docker is configured to take a copy pass.txt file from the host machine, letting it in '/home/ftperab1/ftp/files/pass.txt'. 
SSH docker is configured attending to the following tips:
  - It has openssh-server installed and started. 
  - It has a user called 'dev1' whose password is 'w3ar3h4ck3r2'. 

 'dev1' user's password will never be changed. Moreover, if a team changes it, it will be losing SLa points. 
 
-Flags: 
    Flags will be stored in 'erronkaIgor_ftp_1' docker's '/tmp/flags.txt' file. 

# About exploting:
- The attacker has to inspect the ftp; the credentialas are stored there as plain text. With those credentials, the attacker can log into erronkaIgor_ssh docker and take the flags from /tmp/flags.txt.
- The defender should change 'dev1' user's password. 
  
  Attack performed by Team1 against Team 2. 
  Inspect web page in 10.0.0.104
      We find 'dev1/w3ar3h4ck3r2' credentials.
  ssh -p 8822 dev1@10.0.0.104
        Enter 'w3ar3h4ck3r2' as password
  cat /tmp/flags.txt
     Copy last flags
     Exit
  'ssh -i /home/urko/Deskargak/keyak/team2-sshkey root@10.0.1.1'
  nano /root/xxx.flag
    Paste copied flags. 

  Defense performed by Team4
     'ssh root@10.0.0.104'
     docker exec -it pasapasa_ssh_1 /bin/bash
     passwd dev1
     

# Checker checks:
- Ports to reach dockers are open (FTP:9922; SSH 8822)
- User 'dev1' exists in erronkaIgor_ftp docker. 
- /etc/sshd_config file from pasapasa_ssh docker has not been changed. 
- /usr/local/apache2/htdocs/index.html file's content from pasapasa_web docker has not been changed. 


# License notes
Parts from:
https://github.com/kristianvld/SQL-Injection-Playground



