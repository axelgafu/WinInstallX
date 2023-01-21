# Microsoft Standrd Installer (MSI)


## Silent Installation
Microsoft provides standard installation options as part of the operating system 
installation facilities [^3]; for windows installer 3.0, new `msiexxec.exe` 
parameters can be combined with the standard ones [^2]:

 |  Parameter  | Windows Installer Command-Line Option |
 |:-----------:|---------------------------------------|
 |   /help     | |

Windows installer version 3.0 was released with Windows XP Service Pack 2; 
starting with Windows 8, the OS comes with Windows Installer version 5.0 or 
grater [^4].

*Example* [^1] [^3]
```cmd
msiexec /i c:\path\to\package.msi /quiet /qn /norestart /log c:\path\to\install.log PROPERTY1=value1 PROPERTY2=value2
```

# References
[^1]:. Stackoverflow, "Silent installation of a MSI package", stackoverflow.com, accessed 2023/01/21, [https://stackoverflow.com/questions/8560166/silent-installation-of-a-msi-package](https://stackoverflow.com/questions/8560166/silent-installation-of-a-msi-package)
[^2]:. Microsoft, "Command-Line Options", learn.microsoft.com, accessed 2023/01/21, [https://learn.microsoft.com/en-us/windows/win32/msi/command-line-options?redirectedfrom=MSDN](https://learn.microsoft.com/en-us/windows/win32/msi/command-line-options?redirectedfrom=MSDN)
[^3]:. Microsoft, "Microsoft Standard Installer Command-Line Options", learn.microsoft.com, accessed 2023/01/21, [https://learn.microsoft.com/en-us/windows/win32/msi/standard-installer-command-line-options](https://learn.microsoft.com/en-us/windows/win32/msi/standard-installer-command-line-options)
[^4]:. Microsoft, "Released Versions of Windows Installer", learn.microsoft.com, accessed 2023/01/21, [https://learn.microsoft.com/en-US/windows/win32/msi/released-versions-of-windows-installer](https://learn.microsoft.com/en-US/windows/win32/msi/released-versions-of-windows-installer)
