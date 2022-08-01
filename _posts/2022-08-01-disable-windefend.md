# Disabling Windows Defender the EFFICIENT way
If you use Windows, you sometimes find the built-in antivirus Windows Defender complaining about some random file being harmful. And then one day you get sick of this antivirus and you wanna remove that darn thing, because you don't give an F about antiviruses.

So you search up guides on how to disable Windows Defender forever. But they all involve Safe Mode, but you're running a program that takes long to finish, and you don't want to wait any longer. So what now?

Don't worry: **Mr. GamingWithEvets has a solution!**

## About this method
This method won't require *any* registry or group policy editing. Here's what you need:
- [Process Hacker](https://sourceforge.net/projects/processhacker/files/processhacker2/processhacker-2.39-setup.exe/download) or [PSExec (part of PSTools)](https://download.sysinternals.com/files/PSTools.zip)
- [IOBit Unlocker](https://cdn.iobit.com/dl/unlocker-setup.exe)
- "Show hidden files" turned on in Folder Options

## Here we go baby
**Step 1.** Prepare a Command Prompt ran as SYSTEM  
The steps will be different depending on what program you have installed.

<details>
<summary><b>Guide for Process Hacker</b></summary><br>
Open Process Hacker, then go to Hacker &gt; Run as. Type <code>cmd</code> in the program field and select <code>NT AUTHORITY\SYSTEM</code> as the username. Check "Toggle elevation" and press OK. If you have User Account Control on, press Yes in the UAC prompt.
</details>

<details>
<summary><b>Guide for PSExec</b></summary><br>
In Windows Explorer, navigate to where you have the PSTools executables. Then click on the address bar and type <code>cmd</code> to open the Command Prompt. Now type <code>psexec -accepteula -i -s cmd.exe</code>.
</details>

Make sure to type `whoami` in your system-level Command Prompt instance to verify that it's indeed a system-level Command Prompt. If you don't see `nt authority\system`, you have failed!

**Step 2.** Prepare a rename command  
In your system-level Command Prompt and Windows Explorer, navigate to where the `MsMpEng.exe` executable is. To get its path open Task Manager and in the Processes tab right-click on "Antimalware Service Executable" and select "Properties". The location is the path to the `MsMpEng.exe` executable.

*to be continued, i cant get this done in time :(((((*
