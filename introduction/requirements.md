# ShiftLeft Language Support and Requirements

## Language Support

ShiftLeft Ocular currently supports Java, C# and C/C++ (based on [Joern](https://github.com/octopus-platform/joern)).

ShiftLeft Inspect and Protect analyzes and secures applications written in Java 7+ and C# 6.0. 

Support for other languages is in development. For inquiries, please fill out our [contact form](https://www.shiftleft.io/contact/).

## Requirements

ShiftLeft has specific requirements for:
* [ShiftLeft Ocular](#requirements-for-shiftleft-ocular)
* [ShiftLeft CLI](#shiftleft-cli-requirements)
* [ShiftLeft Inspect](#requirements-for-shiftleft-inspect)
* [ShiftLeft Protect](#requirements-for-shiftleft-protect)
* [Browser](#browser-requirements)

### Requirements for ShiftLeft Ocular

ShiftLeft Ocular runs on top of the Java virtual machine. Please make sure you have a Java Runtime Environment >= 1.8 installed.

### ShiftLeft CLI Requirements

The CLI is used with ShiftLeft Inspect to submit applications for analysis and with ShiftLeft Protect to monitor your applications in runtime. The CLI requires a local installation of a supported Java version. The CLI host must allow outbound connections on the specified port.

Component | Requirement
--- | ---
System | Linux, MacOS X, Windows
JVM | 64-bit **JRE** version **8** (Java 9 is not currently supported). 

To verify that you are running the supported Java version, use the `java -version` command.

### Requirements for ShiftLeft Inspect

ShiftLeft Inspect is a next-generation static application security testing (SAST) solution for applications written in Java and .NET. It provides an accurate and exhaustive exploration and analysis of your unique code and identifies complex vulnerabilities and sensitive data leakage.

#### Java Requirements for ShiftLeft Inspect

ShiftLeft Inspect's Java code analysis is performed on compiled application **bytecode** (not source code). As such, you **must** successfully build your application using a supported build tool **before** you submit the application for analysis. ShiftLeft requires the presence of a supported project build tool to generate security metadata from bytecode. The supported build tool must be installed on the host where you submit an application for analysis. The supported build tools are:

Component | Requirement
--- | ---
System | Linux, MacOS X, Windows
Application Type | **Java 8** or **Java 9**. 
Build environment | Linux or Mac with **Java 8** installed locally and with 16GB of memory available.

Analysis should be performed for each code commit or build of the application. You can automate analysis submissions using your preferred CI/CD system ([Bamboo](../using-inspect-protect/integrating-with-shiftleft/integrating-bamboo-builds.md), CircleCI, [GoCD](../using-inspect-protect/integrating-with-shiftleft/integrating-gocd-builds.md), [Jenkins](../using-inspect-protect/integrating-with-shiftleft/integrating-jenkins-builds/integrating-jenkins-builds.md), [Travis](../using-inspect-protect/integrating-with-shiftleft/integrating-travis-builds.md), [TeamCity](../using-inspect-protect/integrating-with-shiftleft/integrating-teamcity-builds.md), etc.).

To verify that you are running the supported Java version, use the `java -version` command.

#### .NET Requirements for ShiftLeft Inspect

ShiftLeft Inspect's .NET code analysis is performed on **source code** (not on the equivalence of byte code, which is the [CIL](https://en.wikipedia.org/wiki/Common_Intermediate_Language)), and does an actual build of your application as part of the process. Therefore, the system that ShiftLeft Inspect analyzes **must** must be able to successfully build your  application. Remember to restore NuGet packages, if necessary.

The analysis of .NET applications with the following characteristics is supported:

Component | Target Type | Requirement
--- | --- | ---
Specification | | [MSBuild format](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild?view=vs-2017), *i.e.*, a .csproj file.
Language | | C# 7.0
Build environment | **.NET Framework** targets | MSBuild **15.0**. Visual Studio 2017 already comes with MSBuild 15.0. Otherwise, you can [download Visual Studio from Microsoft](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=15).
Build environment | **.NET Core** targets | .NET Core **2.1** or above.

To determine the version of MSBuild installed in your system:

1. In the Windows search bar, type *Developer Command Prompt for VS*.
2. Invoke MSBuild with the version flag: `msbuild /version`.

To verify whether a .NET Framework target can be built with MSBuild 15.0:

1. Open the *Developer Command Prompt for VS*.
2. Navigate to the project location.
3. Restore NuGet packages, if any, using the command `nuget.exe restore MySolution.sln`.
3. Trigger a build using the command `msbuild MyProject.csproj` (and apply additional options, if necessary).

### Requirements for ShiftLeft Protect

ShiftLeft Protect automates the monitoring of production vulnerabilities for applications written in Java and .NET through the deployment of a runtime in-memory Microagent. Support for .NET Core is planned for a future date.

#### Java Requirements for ShiftLeft Protect

ShiftLeft Protect requires a supported 64-bit Java Runtime Environment (JRE). The Microagent memory footprint is a minimal (~50MB). ShiftLeft Protect must be able to download data from, and push metrics to, the ShiftLeft Proxy server over the specified port. If using a firewall, open a connection to a remote service on the specified TCP port.

Component | Requirement
--- | ---
System | Linux, MacOS X, Windows
JVM | 64-bit **JRE** version **7** or higher

To verify that you are running a supported 64-bit JRE, use the `java -version` command.

#### .NET Requirements for ShiftLeft Protect

ShiftLeft Protect requires a Windows operating system with the .NET Framework runtime version 4.5 or later installed, and  works with 64-bit .NET Framework applications. ShiftLeft Protect must be able to download data from, and push metrics to, the ShiftLeft Proxy server over the secure port 443.

The ShiftLeft Protect Windows installer places the Microagent's .NET assemblies into the Global Assembly Cache (GAC). If you are running your application in Microsoft Azure as an AppService, you need to use a Windows Docker Container. See [Windows Container Support in Azure App Service](https://azure.microsoft.com/en-us/blog/announcing-the-public-preview-of-windows-container-support-in-azure-app-service/) for details on this configuration.

Component | Requirement
--- | ---
System | Windows
.NET Framework Runtime | version **4.5** or higher

### Browser Requirements

ShiftLeft supports the following browsers for accessing, viewing and interacting with the ShiftLeft Dashboard:

- Google Chrome (tested with v61, v62)
- Mozilla Firefox (tested with v57, v58b)
- macOS Safari (tested with v11)

Microsoft Edge* is currently not officially supported but has been verified with v41.
