# Disabling Windows Defender the EFFICIENT way
If you use Windows, you sometimes find the built-in antivirus Windows Defender complaining about some random file being harmful. And then one day you get sick of this antivirus and you wanna remove that darn thing, because you don't give an F about antiviruses.

So you search up guides on how to disable Windows Defender forever. But they all involve Safe Mode, but you're running a program that takes long to finish, and you don't want to wait any longer. So what now?

Don't worry: **Mr. GamingWithEvets has a solution!**

## Requirements
This method won't require *any* registry or group policy editing. Here's what you need:
- A TrustedInstaller Command Prompt
- [IObit Unlocker](https://cdn.iobit.com/dl/unlocker-setup.exe)
- "Show hidden files" turned on in Folder Options

## Here we go baby
**Step 1.** Prepare a Command Prompt ran as TrustedInstaller  
There are many different ways to run a TrustedInstaller Command Prompt. Just Google it.

Make sure to type `whoami` in your TrustedInstaller Command Prompt instance to verify that it's indeed a TrustedInstaller Command Prompt. If you see `nt authority\system`, you are good to go!

**Step 2.** Prepare a rename command  
In your TrustedInstaller Command Prompt and Windows Explorer, navigate to where the `MsMpEng.exe` executable is. To get its path open Task Manager and in the Processes tab right-click on "Antimalware Service Executable" and select "Properties". The location is the path to the `MsMpEng.exe` executable.  
After that, type `ren MsMpEng.exe MsMpEng.exe.bak`. **Do not press Enter yet!** We will need this command later.

**Step 3.** Rename `MsMpEng.exe`  
The above rename command doesn't work, as the executable is running in the background. Killing the process doesn't work since Windows complains that it's a system process. So how *do* we kill it?

This is where the IObit Unlocker comes in handy. It can actually kill this process. Right-click the `MsMpEng.exe` executable and choose the IObit Unlocker option. Now in the new window that opens, press Unlock, which will kill the process. Immediately after it's done press Enter on your TrustedInstaller Command Prompt with the rename command to rename the executable, as Windows Defender will restart it if you're not fast enough. If you failed, just redo this step.  
PS: In the previous version of the blog post I mistakenly thought that only a Command Prompt ran as SYSTEM was required, because `MsMpEng.exe`'s owner is SYSTEM. I was wrong though. This updated guide should've corrected it.

**You're done!**  
Hurray! If you completed all three steps without issue, you should see a message in the Virus & threat protection menu of Windows Defender, telling you to restart the Antimalware Service Executable. But it's renamed, so it should *and* will fail miserably. If Windows Defender updates you might need to redo this process.  
To re-enable Windows Defender, just do Steps 1 and 2 again, but type the command `ren MsMpEng.exe.bak MsMpEng.exe` instead. Then press Enter. Then click the Restart now button in Windows Defender. It'll take several seconds for the Antimalware Service Executable to start.

PS: After disabling Windows Defender, it will sometimes nag you to restart the Antimalware Service Executable.

Have fun *not* using Windows Defender! :)))
