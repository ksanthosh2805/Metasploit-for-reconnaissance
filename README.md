# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system

## OUTPUT:

![Screenshot 2024-04-10 092927](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/5e0335e1-7dcf-48aa-9fa2-676fccb7362d)


Invoke msfconsole:

![Screenshot 2024-04-10 093820](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/57be8a40-139a-409a-85b7-c648ae25efa6)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![Screenshot 2024-04-10 093056](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/81611b16-7185-4b9e-8b87-557c361376b3)



## Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![eth54](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/aa5f1e28-6371-437a-a0a7-f54dc4752a2b)


step4: use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

## OUTPUT:

![eth55](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/a592b970-9985-4f9d-a0ac-93a8d0e52598)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l 

![eth56](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/b063722d-0b51-4e82-9014-f80942f4831b)


Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,

## OUTPUT

![Screenshot 2024-04-10 094045](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/7b8dba37-fa28-4ea9-a803-87f0c5ddcbc0)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![eth58](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/f62a9457-53e3-44c6-88a6-ba31add16cfb)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

![eth59](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/2ee491cd-6e1f-419a-b751-dea4c01c8e27)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

![eth510](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/4b68a5d0-0191-453e-b8e1-f72edb61b8af)



Use the set rhosts command to set the parameter and run the module, as follows:

![eth511](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/5f6744e4-e4b1-4235-8e6f-7bfe5222814e)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![eth512](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/9f4af994-e3b4-487a-999c-500526ff8f27)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true

![eth513](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/7acaaa8b-1f18-4932-a6d4-f24230286432)

![eth514](https://github.com/Rajeshanbu/Metasploit-for-reconnaissance/assets/118924713/3c9e60c1-6240-4051-93f5-2aad2f88fc68)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
