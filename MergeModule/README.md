# Generating a Merge Module in WiX

## Merge Module Concept
Merge modules contains the necessary information to instal a subset of a software product. Whereas they do not force software designers to package a standalone feature within them, they would allow to it if that were intended. 
Based on that, merge modules could be considered an installation approximation to the concept of "encapsulation". 

This example is intended to show how merge modules can be used to encapsulate a software piece and it leves to the reader deciding how that could become a solution.


## Example Description
It follows the steps listed below to have a clean merge module definition. All of them are detailed in the WiX Toolset documentation [1].

1. Define the directory structure: Intended to clearly define the directory structure that will be used.
2. Add files to your installer package: Restrict to a single file per component and every component must have its own unique GUID; Visual Studio, generally located under `Tools > Create GUID menu`, or the [https://www.guidgen.com/](https://www.guidgen.com/) site.
3. Tell Windows Installer to install the files: A merge module is a wrapper of a file group, installing files is done in the MSI project by using the `Merge` element in the following way (for example):
```xml #2,5
    <Directory Id="TARGETDIR" Name="SourceDir">
      <Merge Id="abcMergeModule" Language="1033" SourceFile="..\MergeModule\bin\Release\MergeModule.msm" DiskId="1" />
    </Directory>
    
    <Feature Id="AbcFeature" Title="ABC Program" Level="1">
      <MergeRef Id="abcMergeModule" />
    </Feature>
```
The merge module is invoked by the `Feature`tag. The `Directory` tag is required by the `Merge` tag since the later is child of the former [3]. Consider the `Directory` tag as an "overloaded" entity whose purpose in this example is to be the driver to access the merge module. The merge module will override the directory structure creation and thus, the directory name above will be ignored.

It is possible to have WiX using the manufacturer name and product name specified in the main installer [4]. The following example shows how this has been done in this sample project:
```xml #3-4
    <Directory Id="TARGETDIR" Name="SourceDir">
      <Directory Id="ProgramFilesFolder">
        <Directory Id="MANUFACTURERDIR" Name="!(bind.property.Manufacturer)">
          <Directory Id="PRODUCTDIR" Name="!(bind.property.ProductName)">
            <Merge Id="abcMergeModule" Language="1033" SourceFile="..\MergeModule\bin\Release\MergeModule.msm" DiskId="1" />
            <Merge Id="mergeModule2" Language="1033" SourceFile="..\MergeModule2\bin\Release\MergeModule2.msm" DiskId="1" />
          </Directory>
        </Directory>
      </Directory>
    </Directory>
```
In the above example `MANUFACTURERDIR` and `PRODUCTDIR` are initialized with the values specified for `Manufacturer` and `Name` attributes of the `Product` tag in the MSI installer; see Product.wxs from "InstallerMsi" sample project in this repository.
```xml
<Product 
    Name="SampleInstaller" 
    Language="1033" 
    Version="1.0.0.0" 
    Manufacturer="axelgafu" 
    Id="{7C056D93-524B-45E2-B11D-564946A08608}" 
    UpgradeCode="{68282F11-8C3B-4581-91F6-EE3D7135481D}">
```

# References
1. WiX Toolset, "How To: Add a File To Your Installer", wixtoolset.org, accessed 2022/01/14, [https://wixtoolset.org/docs/v3/howtos/files_and_registry/add_a_file/](https://wixtoolset.org/docs/v3/howtos/files_and_registry/add_a_file/)
2. WiX Toolset, "How To: Generate a GUID", wixtoolset.org, accessed 2022/01/14, [https://wixtoolset.org/docs/v3/howtos/general/generate_guids/](https://wixtoolset.org/docs/v3/howtos/general/generate_guids/)
3. WiX Toolset, "Merge Element", wixtoolset.org, accessed 2022/01/14, [https://wixtoolset.org/docs/v3/xsd/wix/merge/](https://wixtoolset.org/docs/v3/xsd/wix/merge/)
4. Stackoverflow, "Wix Installer - how can I show the value of [Manufacturer] in the install path?", stackoverflow.com, accessed 2022/01/15, [https://stackoverflow.com/questions/16946701/wix-installer-how-can-i-show-the-value-of-manufacturer-in-the-install-path](https://stackoverflow.com/questions/16946701/wix-installer-how-can-i-show-the-value-of-manufacturer-in-the-install-path)
5. Khadeer Md, "Wix Creating Merge Modules MSM and MSI.", medium.com, 2019/07/15,  [https://medium.com/@kmdkhadeer/wix-creating-merge-modules-msm-and-msi-354fdd29a26e](https://medium.com/@kmdkhadeer/wix-creating-merge-modules-msm-and-msi-354fdd29a26e)
