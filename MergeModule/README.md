# Generating a Merge Module in WiX

It follows the steps listed below to have a clean merge module definition. All of them are detailed in the WiX Toolset documentation [1].

1. Define the directory structure: Intended to clearly define the directory structure that will be used.
2. Add files to your installer package: Restrict to a single file per component and every component must have its own unique GUID; Visual Studio, generally located under `Tools > Create GUID menu`, or the [https://www.guidgen.com/](https://www.guidgen.com/) site.
3. Tell Windows Installer to install the files: A merge module is a wrapper of a file group, installing files is done in the MSI project by using the `Merge` element in the following way (for example):
```xml
    <Directory Id="TARGETDIR" Name="SourceDir">
      <Merge Id="abcMergeModule" Language="1033" SourceFile="..\MergeModule\bin\Release\MergeModule.msm" DiskId="1" />
    </Directory>
    
    <Feature Id="AbcFeature" Title="ABC Program" Level="1">
      <MergeRef Id="abcMergeModule" />
    </Feature>
```
The merge module is invoked by the `Feature`tag. The `Directory` tag is required by the `Merge` tag since the later is child of the former [3]. Consider the `Directory` tag as an "overloaded" entity whose purpose in this example is to be the driver to access the merge module. The merge module will override the directory structure creation and thus, the directory name above will be ignored.


# References
1. WiX Toolset, "How To: Add a File To Your Installer", wixtoolset.org, accessed 2022/01/14, [https://wixtoolset.org/docs/v3/howtos/files_and_registry/add_a_file/](https://wixtoolset.org/docs/v3/howtos/files_and_registry/add_a_file/)
2. WiX Toolset, "How To: Generate a GUID", wixtoolset.org, accessed 2022/01/14, [https://wixtoolset.org/docs/v3/howtos/general/generate_guids/](https://wixtoolset.org/docs/v3/howtos/general/generate_guids/)
3. WiX Toolset, "Merge Element", wixtoolset.org, accessed 2022/01/14, [https://wixtoolset.org/docs/v3/xsd/wix/merge/](https://wixtoolset.org/docs/v3/xsd/wix/merge/)
