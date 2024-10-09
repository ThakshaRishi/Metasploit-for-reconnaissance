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

![Screenshot 2024-10-09 081704](https://github.com/user-attachments/assets/d013af5b-1e00-44b9-a974-78a9d85ff20c)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:

```
systemctl start postgresql

msfdb init
```

Invoke msfconsole:

## OUTPUT:

![image](https://github.com/user-attachments/assets/22c4481d-b8a4-49e0-aeed-cfa958815c11)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
![image](https://github.com/user-attachments/assets/3bde6bd3-2e3a-4831-8f4d-faa3ed29ee6c)

Port Scanning: Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:
![image](https://github.com/user-attachments/assets/07371d29-823c-4a15-8448-3973af8837d5)

step4: use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

## OUTPUT:

![image](https://github.com/user-attachments/assets/351d8eb6-42d4-4703-a9a3-09032d8a450e)

![image](https://github.com/user-attachments/assets/620576c2-423f-4c42-9624-281ef841821d)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:
![image](https://github.com/user-attachments/assets/effce39e-cfc5-4de6-add8-2a990edb0b34)

Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

## OUTPUT:
![image](https://github.com/user-attachments/assets/462d3f3e-8130-48f9-9cda-3fd738416303)

The info command provides information regarding a module or platform
## OUTPUT:
![image](https://github.com/user-attachments/assets/8ca3da14-2d01-4b05-bf33-782b354ddb5c)

![image](https://github.com/user-attachments/assets/00525a0b-767f-4c16-b175-7e62b4c8ead4)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
```
systemctl start postgresql
```
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
![image](https://github.com/user-attachments/assets/18c1291c-8970-4a4a-a6c1-5288294f20b0)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

## OUTPUT:
![image](https://github.com/user-attachments/assets/3c670fbe-5718-4b35-b6b0-d995b5acea26)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

## OUTPUT:




Use the set rhosts command to set the parameter and run the module, as follows:

## OUTPUT:

![image](https://github.com/user-attachments/assets/6ed571eb-7588-4eea-92c5-e78068455372)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
![image](https://github.com/user-attachments/assets/6a837a6a-4dab-404d-b4a4-a9fab286c7ce)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
```
set PASS_FILE /usr/share/wordlists/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS
```
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
```
set BLANK_PASSWORDS true
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/acb336fc-4f10-4a89-aa8e-004163937dfb)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
