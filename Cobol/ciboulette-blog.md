# Ciboulette blog

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

We are in year 2024. Cobol started in 1959.

This week I took the course "From Zero to **Cobol**" and rather found myself being a modern day archaeologist of early IT artefacts...

![logo](../pix/cob-cave.webp)

Training, means having appropriate tools to practice. VS Code proved again to be an incredible Swiss army knife. Here is my exploring outcome.

# Possible paths to go

- [-] Work on **Mainframe** - 😖I don't have. Online courses like Coursera say to use free plans on IBM Z XPLORE but the offer is not available anymore to get a free Z-ID.

- [-] Work with the open source Hercules **emulator** http://www.hercules-390.org, or **docker** images https://hub.docker.com/r/rattydave/docker-ubuntu-hercules-mvs are 🙁not much helpful for a learning developer.

- [-] Work by **transpiling** Cobol into C# with Otterkit COBOL from Keyth Taylor. Interesting but 😔not for main usage case.

- [!] Work on **WSL**, and **VS Code**. This used to be the 🙂recommended path. WSL let the linux original libraries and programs to be used. It **works** well, many VS Code extensions are built atop this stack. So you need to 'open WSL in folder ...' in VS Code. It certainly works, but involves some **gym** between the 2 OS and a certain **overhead**.

- [V] Work on **Windows only**. This used to be a 😱perilous path https://www.arnoldtrembley.com/GnuCOBOL.htm but recently a 😃great package can be found there https://superbol.eu/. It's a **.MSI** that saves you all compilation and integration worries on the Win platform.
	_I just made a slim patch to reach the desired state: Debug, EXEC SQL, Unit test._

1. Go to Superbol website
	https://superbol.eu/software/gnucobol-windows-installer/aio-release/
	and grab the machine release `gnucobol-3.2-aio-20240306-machine.msi`
1. Install the .MSI
2. Go to my github
	https://github.com/viiinzzz/gnucobol-3.2-aio-20240306-machine-patch-vinz
1. Download ZIP and extract to your `C:`
2. Make sure your VS Code project has the appropriate configurations as can be found in
	`C:\Program Files\GnuCOBOL\.vscode`

My 🩹patch [gnucobol-3.2-aio-20240306-machine-patch-vinz] consists of:
- headers
- commands
- jar
- config
- json

_remark: I picked up these .h from https://github.com/lattera/glibc/blob/master_

- [V] Superbol comes with `gixsql` a preprocessor for `EXEC SQL` sections.
However when processing `EXEC SQL` the regular `cobc` get tangled with the arguments leading to failure.

I'm not sure how to contribute to their repo https://github.com/OCamlPro/superbol-vscode-debug

I just wrote 3 additional commands, put them into the bin folder:
`C:\Program Files\GnuCOBOL\bin`

Since it is in the path, you can therefore invoke `cobc-sql`  (compile) or `cobcrun-sql` (compile and run), `cobolcheck` (Unit test) from wherever you want !!! 

Another desired feature is the ability to **debug**.
- [-] I used successfully the extension `COBOL debugger` in VS Code + WSL. But as told earlier, I want to avoid going through WSL.
- [V] Now with GnuCOBOL in Windows itself, I also installed the twin extension from the same company OCamlPro called `SuperBOL Studio OSS` and it has compile and debug tasks that work great given my patch is installed. That extension is a prerelease, I bet they will fix the small mis soon.

Finally I would like to perform **unit testing**.
https://github.com/openmainframeproject/cobol-check
The latest distribution is available there:
https://github.com/openmainframeproject/cobol-check/blob/Developer/build/distributions/cobol-check-0.2.10.zip

- [-] Cobol Check Extension from Open Mainframe Project. While in WSL this extension worked well and offered integration of Cobol Check into VS Code test runner plus a nice red/green visual summary. However going the GnuCOBOL in Windows way, the extension is broken. Hence forget it. commandline `cobolcheck -p THETEST` output is good enough.

# Other useful Cobol extensions

- [V] COBOL Language Support from Broadcom
- [V] COBOL Folding from Zokugun

# GnuCOBOL

Help for GnuCOBOL `cobc` command can be found here https://gnucobol.sourceforge.io/doc/gnucobol.html


# Cobol to C# transpilation

I found it is an attractive way because I am primarily a C# dev, hence it could be nice to leverage legacy Cobol code right into a C# app. So I gave it a try. While it could help, the use case may be quite narrow. So I just keep it in mind.

Interesting blog to read https://www.productperfect.com/blog/convert-cobol-to-c-sharp

The proposition: Otterkit https://github.com/otterkit/otterkit-cobol

## Setup

```cmd
dotnet new install Otterkit.Templates::1.7.50
dotnet tool install --global Otterkit --version 1.0.80
```

## Transpile

```
otterkit new app
otterkit build -e hello.cbl -free
```
**!!!ERRORS**

_Fix_
> downgrade templates
> dotnet new install Otterkit.Templates::1.0.45-alpha
> change csproj net8.0 and otterkit.library to version 1.0.45-alpha

```csproj
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net8.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
    <Optimize>true</Optimize>
    <Deterministic>true</Deterministic>
    <PublishSingleFile>true</PublishSingleFile>
    <SelfContained>false</SelfContained>
    <IncludeNativeLibrariesForSelfExtract>true</IncludeNativeLibrariesForSelfExtract>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Otterkit.Library" Version="1.0.45-alpha" />
  </ItemGroup>

</Project>
```

--> compile again
`otterkit build -e hello.cbl -free`

-->execute
`C:\git\cobol\samples>.otterkit\Build\OtterkitExport.exe`

> HELLO WORLD

Happy !!!

