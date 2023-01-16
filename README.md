# Windows Installer Experiment
Bootstrapper example that generates a setup.exe installation file (work-in-progress). For additional examples, it is recommended to visit kurtanr's repository for installers examples [2].

See the following video

[![Creating Professional Installations with WiX | Tips](https://img.youtube.com/vi/usOh3NQO9Ms/0.jpg)](https://www.youtube.com/watch?v=usOh3NQO9Ms&ab_channel=Synergex)

Throughout this repository's folders you will find more redme files like this to explain how Windows Installer XML (WiX) technology can be used to create a sample installer by using customized GUI, installation modules called ["merge modules"](MergeModule), Microsoft Installer to [generate MSI](InstallerMsi), the [bootstrapper technology](BootstrapperExperiment), ad hoc installation routines call ed "custom actions" and maybe more.

## Installation
Chose the visual studio plugin that matches your IDE version [1]. WiX toolset is required and installing .NET Framework 3.5 is required by the toolset. The instructions to install it are in reference [3].

1. Install .NET Framework 3.5 by following the instructions from reference [3]
2. Download development builds from WiX Toolset page: [https://wixtoolset.org/docs/wix3/](https://wixtoolset.org/docs/wix3/)
3. Install Visual Studio plugin from the marketplace: [https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset)

# References
1. Visual Studio Marketplace, "WiX Toolset Build Tools", marketplace.visualstudio.com, accessed on 2023/01/13, [https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset)
2. kurtanr, "WiX Installer Examples", github.com, accessed on 2023/01/13, [https://github.com/kurtanr/WiXInstallerExamples](https://github.com/kurtanr/WiXInstallerExamples)
3. "Install the .NET Framework 3.5 on Windows 11, Windows 10, Windows 8.1, and Windows 8", learn.microsoft.com, accessed on 2023/01/13, [https://learn.microsoft.com/en-US/dotnet/framework/install/dotnet-35-windows](https://learn.microsoft.com/en-US/dotnet/framework/install/dotnet-35-windows)
