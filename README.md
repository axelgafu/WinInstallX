# Windows Installer Experiment
Bootstrapper example that generates a setup.exe installation file (work-in-progress). For additional examples, it is recommended to visit kurtanr's repository for installers examples [2].

See the following video
<iframe
    width="640"
    height="480"
    src="https://www.youtube.com/watch?v=usOh3NQO9Ms&ab_channel=Synergex?autoplay=0"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Installation
Chose the visual studio plugin that matches your IDE version [1]. WiX toolset is required and installing .NET Framework 3.5 is required by the toolset. The instructions to install it are in reference [3].

1. Install .NET Framework 3.5 by following the instructions from reference [3]
2. Download development builds from WiX Toolset page: [https://wixtoolset.org/docs/wix3/](https://wixtoolset.org/docs/wix3/)
3. Install Visual Studio plugin from the marketplace: [https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset)

# References
1. Visual Studio Marketplace, "WiX Toolset Build Tools", marketplace.visualstudio.com, accessed on 2023/01/13, [https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset)
2. kurtanr, "WiX Installer Examples", github.com, accessed on 2023/01/13, [https://github.com/kurtanr/WiXInstallerExamples](https://github.com/kurtanr/WiXInstallerExamples)
3. "Install the .NET Framework 3.5 on Windows 11, Windows 10, Windows 8.1, and Windows 8", learn.microsoft.com, accessed on 2023/01/13, [https://learn.microsoft.com/en-US/dotnet/framework/install/dotnet-35-windows](https://learn.microsoft.com/en-US/dotnet/framework/install/dotnet-35-windows)