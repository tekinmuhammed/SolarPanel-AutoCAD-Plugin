# AutoCAD Solar Panel Plugin with C#
### C# Visual Studio Project Template for an AutoCAD Plugin.
This repository provides a C# Visual Studio Project Template for developing AutoCAD plugins. These templates enable you to quickly start a C# project for an AutoCAD plugin in Visual Studio. They are designed to automatically launch the specified version of AutoCAD and load the assembly when debugging begins.

The AutoCAD R24 Csharp Project Template is intended for use with AutoCAD versions prior to 2025 (targeting .NET Framework).
The AutoCAD R25 Csharp Project Template is designed for AutoCAD 2025 and later (targeting .NET 8).
For AutoCAD 2016 and later, it is essential to set the LEGACYCODESEARCH system variable to 1 to enable the automatic loading of the assembly.

### Editing the template files
In order for the template to work, the paths to the acad.exe file and to the AutoCAD libraries must match those on the local computer.

### AutoCAD R24 Csharp Project Template

#### AutocadR24Plugin.csproj
The MSBuild project file (.csproj) is an xml file that describe and control the process of generation of the applications.

The path to the acad.exe file of the AutoCAD version to be launched at debugging startup must be consistent with that of the local computer.
```	xml
		<!-- Change the path to the installation folder of the targeted AutoCAD version -->
		<StartProgram>C:\Program Files\Autodesk\AutoCAD 2022\acad.exe</StartProgram>
```
The paths to the AutoCAD libraries referenced by the project must be consistent with those of the local computer.
``` xml
	    <!-- Change the paths to the targeted AutoCAD libraries -->
		<Reference Include="AcCoreMgd">
			<HintPath>C:\ObjectARX 2022\inc\AcCoreMgd.dll</HintPath>
			<Private>False</Private>
		</Reference>
		<Reference Include="AcDbMgd">
			<HintPath>C:\ObjectARX 2022\inc\AcDbMgd.dll</HintPath>
			<Private>False</Private>
		</Reference>
		<Reference Include="AcMgd">
			<HintPath>C:\ObjectARX 2022\inc\AcMgd.dll</HintPath>
			<Private>False</Private>
		</Reference>
```
It is preferable that the required version of .NET Framework is the one installed by the targeted AutoCAD version (see [this page](https://help.autodesk.com/view/OARX/2022/ENU/?guid=GUID-450FD531-B6F6-4BAE-9A8C-8230AAC48CB4)).
``` xml
		<!-- Change the targeted .NET Framework version -->
		<TargetFrameworkVersion>v4.8</TargetFrameworkVersion>
```
#### MyTemplate.vstemplate
This file describes the template.

Name and Desription of the template.
``` xml
		<!-- Change the name and description as desired -->
		<Name>AutoCAD R24 Plugin</Name>
		<Description>AutoCAD R24 Plugin (.NET Framework)</Description>
```
Default name of the assembly.
``` xml
		<!-- Change the default project name as desired -->
		<DefaultName>AutocadR24Plugin</DefaultName>
```

### AutoCAD R25 Csharp Project Template

#### Properties\launchSettings.json
The path to the acad.exe file of the AutoCAD version to be launched at debugging startup must be consistent with that of the local computer.
```	json
{
  "profiles": {
    "$safeprojectname$": {
      "commandName": "Executable",
      "executablePath": "C:\\Program Files\\Autodesk\\AutoCAD 2025\\acad.exe",
      "commandLineArgs": "/nologo /b \"start.scr\""
    }
  }
}
```

#### AutocadR25Plugin.csproj
The MSBuild project file (.csproj) is an xml file that describe and control the process of generation of the applications.

The paths to the AutoCAD libraries referenced by the project must be consistent with those of the local computer.
``` xml
	<!-- Change the paths to the targeted AutoCAD libraries -->
	<ItemGroup>
		<Reference Include="accoremgd">
			<HintPath>F:\ObjectARX 2025\inc\AcCoreMgd.dll</HintPath>
			<Private>False</Private>
		</Reference>
		<Reference Include="Acdbmgd">
			<HintPath>F:\ObjectARX 2025\inc\AcDbMgd.dll</HintPath>
			<Private>False</Private>
		</Reference>
		<Reference Include="acmgd">
			<HintPath>F:\ObjectARX 2025\inc\AcMgd.dll</HintPath>
			<Private>False</Private>
		</Reference>
	</ItemGroup>
```
To reference Windows Forms or WPF libraries, you have to add the following nodes to the first PropertyGroup node.
``` xml
<UseWindowsForms>true</UseWindowsForms>
<!-- and/or -->
<UseWPF>true</UseWPF>
```
To disable some .NET Core specific features such as Nullable References, remove the following node or replace `enable` with `disable`.
``` xml
<Nullable>enable</Nullable>
```

#### MyTemplate.vstemplate
This file describes the template.

Name and Desription of the template.
``` xml
		<!-- Change the name and description as desired -->
		<Name>AutoCAD R25 Plugin</Name>
		<Description>AutoCAD R25 Plugin (.NET 8)</Description>
```
Default name of the assembly.
``` xml
		<!-- Change the default project name as desired -->
		<DefaultName>AutocadR25Plugin</DefaultName>
```
