# sticky-keys-scanner

A PowerShell function that scans for the existence of Sticky Key backdoors.

You can either import and run this PowerShell function locally on the suspected computer
or use PowerShell remoting to run the scanner across multiple computers using the Invoke-Command
cmdlet.

Example usage:


What are Sticky Key backdoors?

Sticky Keys are part of the Windows operating system and are designed for people with difficulty
holding down two or more keys simultaneously.  There are two primary methods for installing the backdoor.

(1) Attackers replace accessibility programs (sethc.exe, utilman.exe, osk.exe, narrator.exe, magnify.exe, 
displayswitch.exe) with programs that provide system-level shell access such as explorer.exe, cmd.exe, 
or powershell.exe. and/or

(2) Attackers modify the registry to set cmd.exe and other shell programs as debuggers for the above listed
accessibility programs.  For example:  REG ADD "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File
Execution Options\sethc.exe" /v Debugger /t REG_SZ /d "c:\windows\system32\cmd.exe"

Once installed, an attacker can access the backdoor by pressing the appropriate accessibility sticky key.
For example, windows_key+u key combination would be pressed by the attacker to gain access to a system-level command 
prompt if the utilman.exe program was targeted.

Credits:
http://files.sans.org/summit/Threat_Hunting_Incident_Response_Summit_2016/PDFs/Proactive-APT-Hunting-Style-Joshua-Theimer-and-Hao-Wang-EY.pdf
http://carnal0wnage.attackresearch.com/2012/04/privilege-escalation-via-sticky-keys.html
https://zachgrace.com/2015/03/23/hunting-sticky-keys-backdoors.html
https://www.crowdstrike.com/blog/registry-analysis-with-crowdresponse/
http://www.jonathanmedd.net/2014/02/testing-for-the-presence-of-a-registry-key-and-value.html
