# Shady-Hook
Hooking API calls of a Ransomware using [Microsoft Detours](https://www.microsoft.com/en-us/research/project/detours/).

### Summary
In this project, I developed a DLL and an injector that injects the DLL into a ransomware. The DLL hooks the API CreateFileW() that is called by the ransomware to open any file before encrypting it. The control goes to a custom function MyCreateFileW() within the DLL, which alters the call in such a way that it will always return an invalid handle value, thus making the ransomware unable to open any file. **This prevents the ransomware from encrypting the files in the system.** 

### API hooking
API hooking is a powerful technique that allows someone to hijack a function and redirect it to a custom one. Anything can be done in the custom function before passing control back to the original API. A key motivation for hooking, is not only to contribute to advanced functionalities, but also to inject user-supplied code for debugging purposes. The same can be used for **malware behavioral analysis**.

**Advantages of hooking:**
1.	API function's monitoring
2.	Debugging and reverse engineering
3.	Peering inside operating system
4.	Extending originally offered functionalities 

### DLL injection
DLL injection is the process of inserting code into a running process. The Windows API offers a number of functions that allow us to attach onto and manipulate other programs for debugging purposes which can be leveraged to perform DLL Injection. 

### Learning Resources

* [Code Project - Article on API hooking](https://www.codeproject.com/Articles/2082/API-hooking-revealed)
* [Open Security Research - Article on DLL injection basics](http://blog.opensecurityresearch.com/2013/01/windows-dll-injection-basics.html)
* [Zer0Mem0ry - Video on DLL injection](https://www.youtube.com/watch?v=g_Xx90wyk0c)
