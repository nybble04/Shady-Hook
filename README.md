# Shady-Hook
Hooking API calls of a Ransomware using Microsoft Detours.

**API hooking** is a powerful technique that allows someone to hijack a function and redirect it to a custom one. Anything can be done in the custom functions before passing control back to the original API. By doing this, the parameters can be modified, the original program can be tricked if you choose to return an error code when really it should be successful, and so on. A key motivation for hooking, is not only to contribute to advanced functionalities, but also to inject user-supplied code for debugging purposes. 

**Advantages of hooking:**
1.	API function's monitoring
2.	Debugging and reverse engineering
3.	Peering inside operating system
4.	Extending originally offered functionalities 

**DLL injection** is the process of inserting code into a running process. The Windows API actually offers a number of functions that allow us to attach and manipulate into other programs for debugging purposes. We'll leverage these methods to perform our DLL Injection. 

In this project, I developed a DLL and an injector that injects the DLL into a ransomware. The DLL hooks the API CreateFileW() that will be called by the ransomware to open any file before encrypting it. The custom function MyCreateFileW() in the DLL, alters the call in such a way that it will always return an invalid handle value thus making the ransomware unable to open any file. This prevents the ransomware from encrypting the files in the system. 

The same can be used for any other remote process in a windows system for sniffing or spying, or for **malware behavioral analysis**.


### Prerequisites

* [Visual Studio IDE] (https://visualstudio.microsoft.com/vs/)
* [Detours] (https://www.microsoft.com/en-us/research/project/detours/) , (https://github.com/Microsoft/Detours)
* VirtualBox / VMware with a Windows Virtual Machine
* A ransomware, I used shade.exe


### Cool resources I used while learning

* (https://www.codeproject.com/Articles/2082/API-hooking-revealed)
* (http://blog.opensecurityresearch.com/2013/01/windows-dll-injection-basics.html)
* (https://www.youtube.com/watch?v=g_Xx90wyk0c)


