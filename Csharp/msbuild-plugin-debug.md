# Advanced MSBuild : early deployment of a plugin during Debug build

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

During the Debug phase, multiple build/debug/fix iterations may be needed in a complex solution where a technical debt was accumulated, or where a difficult to debug legacy is present, especially where a loose plugin architecture is used.

Plugin architecture is great because it is open and expandable, however debugging highly introspective and decorrelated code can be tricky.

As a developer, you quickly feel you should do better than the basic build process to save time, so you will be able to focus on the solution bugs. That was the driving idea.

However MSBuild is quite coarse, so I offer a few insights to help reach a more comfortable Debug build process. 

![pix](../pix/plugin-debug-build.png)

<kbd>.csproj</kbd>

```xml
<?xml version="1.0" encoding="utf-8"?>

<!--
This .csproj exerpt demonstrates how to leverage msbuild and some of its extensions to perform atypical build tasks
-->

<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

<!--
MSBuild Extension Pack to be added with Nuget
-->

  <Import Project="..\..\packages\MSBuild.Extension.Pack.1.9.1\build\net40\MSBuild.Extension.Pack.targets" Condition="Exists('..\..\packages\MSBuild.Extension.Pack.1.9.1\build\net40\MSBuild.Extension.Pack.targets')" />

  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />

  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />

  <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">

    <Message Text="=== Check MSBuild.Extension.Pack ===" Importance="High" />

    <PropertyGroup>

      <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>

    </PropertyGroup>

    <Error Condition="!Exists('..\..\packages\MSBuild.Extension.Pack.1.9.1\build\net40\MSBuild.Extension.Pack.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\..\packages\MSBuild.Extension.Pack.1.9.1\build\net40\MSBuild.Extension.Pack.targets'))" />

  </Target>




<!--
in the following Target, I specify a Copy task to be performed before the build.

Observe the Message statement, which allow to report to the build console what we are doing, before or after the task itself.
This is much useful to troubleshoot complex build mechanics.
You will see in some further sections Message where I include &#xD;&#xA; to break lines, indeed the build console is sometimes to much condensed to easily spot where the build process has gone, so it is helpful to give some space around critical steps you want to keep an eye on.

here, it is a hotfix to get WCFCore work in a legacy .Net Framework application
-->

  <Target Name="CopySPSM" BeforeTargets="Build">

    <Message Text="=== Copy System.Private.ServiceModel ===" Importance="High" />

    <Copy SourceFiles="G:\devnetx\packages\System.Private.ServiceModel.4.10.3\lib\netstandard2.0\System.Private.ServiceModel.dll" DestinationFolder="$(OutputPath)" />

  </Target>




<!--
in the following Target, I prepare a dll landscape for a plugin distribution

I execute a powershell inline script that runs a oneliner dos command.
The tricky part here is to escape appropriately and to concatenate it all.
Escaping characters involves several levels (Dos -> Powershell -> Xml).
This proved to be very annoying to put up, but once tuned, the build process is seamless.

&amp;&amp; for &&
\&quot; for "

enclose paths into "..." thus \&quot;...\&quot;
-->

  <Target Name="CopyDllsToDist" AfterTargets="CopySPSM">

    <Message Importance="High" Text="&#xD;&#xA;    &#xD;&#xA;    &#xD;&#xA;=== Copy ThePlugin dlls to dist ===&#xD;&#xA;&#xD;&#xA;    ...&#xD;&#xA;" />

    <Exec Command="powershell -Command &quot;Start-Process cmd -ArgumentList('/C', ' (if not exist \&quot;$(ProjectDir)$(OutDir)dist\extralibs\&quot; mkdir \&quot;$(ProjectDir)$(OutDir)dist\extralibs\&quot;)  &amp;&amp;(if not exist \&quot;$(ProjectDir)$(OutDir)dist\fr\&quot; mkdir \&quot;$(ProjectDir)$(OutDir)dist\fr\&quot;)  &amp;&amp;copy /Y \&quot;$(ProjectDir)$(OutDir)*.dll\&quot; \&quot;$(ProjectDir)$(OutDir)dist\extralibs\&quot;  &amp;&amp;copy /Y \&quot;$(ProjectDir)$(OutDir)fr\ThePlugin.resources.dll\&quot; \&quot;$(ProjectDir)$(OutDir)dist\fr\&quot;  &amp;&amp;copy /Y \&quot;$(ProjectDir)$(OutDir)*.config\&quot; \&quot;$(ProjectDir)$(OutDir)dist\extralibs\&quot;  &amp;&amp;copy /Y \&quot;$(ProjectDir)$(OutDir)*.pdb\&quot; \&quot;$(ProjectDir)$(OutDir)dist\extralibs\&quot;  &amp;&amp;del /s \&quot;$(ProjectDir)$(OutDir)dist\extralibs\IDontWanThis.*\&quot;  &amp;&amp;del /s \&quot;$(ProjectDir)$(OutDir)dist\extralibs\IDontWantThat.*\&quot;  &amp;&amp;del /s \&quot;$(ProjectDir)$(OutDir)dist\extralibs\NoThanks.dll\&quot;  &amp;&amp;del /s \&quot;$(ProjectDir)$(OutDir)dist\extralibs\NoThanks.dll.config\&quot;  &amp;&amp;del /s \&quot;$(ProjectDir)$(OutDir)dist\extralibs\NoThanks.pdb\&quot;  &amp;&amp;move /Y \&quot;$(ProjectDir)$(OutDir)dist\extralibs\LetsFlattenThis.*\&quot; \&quot;$(ProjectDir)$(OutDir)dist\&quot; ')&quot;" />

    <Message Importance="High" Text="&#xD;&#xA;    &#xD;&#xA;    ThePlugin dlls copied to $(ProjectDir)$(OutDir)dist&#xD;&#xA;    &#xD;&#xA;&#xD;&#xA;" />

  </Target>




<!--
In 'Debug' configuration, I want an early deployment of the plugin to the program files

a message is displayed if adjourning because not in debug. See the condition.

next step is critical and you will see, is protected by user confirmation
-->

  <Target Name="MessageCopyDllsToProg" AfterTargets="CopySPSM" Condition="'$(Configuration)' != 'Debug'">

    <Message Importance="High" Text="&#xD;&#xA;    &#xD;&#xA;    &#xD;&#xA;=== Copy ThePlugin dlls to program files ===&#xD;&#xA;&#xD;&#xA;    ADJOURNED.&#xD;&#xA;&#xD;&#xA;    Happens only for Configuration 'Debug'&#xD;&#xA;&#xD;&#xA;&#xD;&#xA;" />

  </Target>



  <Target Name="AskStopTheProg" AfterTargets="CopyDllsToDist" Condition="'$(Configuration)' == 'Debug'">

<!--
grasp the developer attention, emitting a beep, indeed next dialog appears minimized
-->
    <MSBuild.ExtensionPack.UI.Console TaskAction="Beep" Repeat="1" Duration="250" Frequency="425" />

<!--
ask confirmation to deploy
-->
    <MSBuild.ExtensionPack.UI.Dialog TaskAction="Show" Text="Stop TheProg to Copy ThePlugin Debug dlls to Program Files" Button1Text="Continue" Button2Text="Cancel" Title="ThePlugin Debug Deploy">

      <Output TaskParameter="ButtonClickedText" PropertyName="answerStopTheProg" />

    </MSBuild.ExtensionPack.UI.Dialog>

  </Target>




<!--
check the previous dialog returned a Continue answer
then elevate powershell to kill the program that will receive the plugin update

We would not kill the prog if not authorized by the user otherwise work could be lost.
-->

  <Target Name="StopTheProgAndCopyDllsToProg" AfterTargets="AskStopTheProg" Condition="'$(Configuration)' == 'Debug' And '$(answerStopTheProg)' == 'Continue'">

    <Message Importance="High" Text="&#xD;&#xA;    &#xD;&#xA;    &#xD;&#xA;=== Stopping TheProg ===&#xD;&#xA;&#xD;&#xA;    ...&#xD;&#xA;" />

    <Exec Command="powershell -Command &quot;Stop-Process -Name TheProg -Force" ContinueOnError="WarnAndContinue" />

    <Message Importance="High" Text="&#xD;&#xA;    &#xD;&#xA;    Stopped TheProg.&#xD;&#xA;&#xD;&#xA;&#xD;&#xA;" />

    <PropertyGroup>

<!--
That's the way to declare a custom variable that can later be refered to as $(TheProg) in a string
-->
      <TheProg>C:\Program Files\Thecorp\Theprog\</TheProg>

    </PropertyGroup>

    <Message Importance="High" Text="&#xD;&#xA;    &#xD;&#xA;    &#xD;&#xA;=== Copy ThePlugin Debug dlls to $(TheProg) ===&#xD;&#xA;&#xD;&#xA;    ...&#xD;&#xA;" />

<!--
then elevate powershell to copy the prepared plugin distribution to program files
-->

    <Exec Command="powershell -Command &quot;Start-Process cmd -ArgumentList('/C', ' @echo off  &amp;&amp;echo Copy ThePlugin Debug dlls to $(TheProg) &amp;&amp;(if not exist \&quot;$(TheProg)extralibs\&quot; mkdir \&quot;$(TheProg)extralibs\&quot;)  &amp;&amp;(if not exist \&quot;$(TheProg)fr\&quot; mkdir \&quot;$(TheProg)fr\&quot;)  &amp;&amp;copy /Y \&quot;$(ProjectDir)$(OutDir)dist\extralibs\*.*\&quot; \&quot;$(TheProg)extralibs\&quot;  &amp;&amp;copy /Y \&quot;$(ProjectDir)$(OutDir)dist\*.*\&quot; \&quot;$(TheProg)&quot;  &amp;&amp;copy /Y \&quot;$(ProjectDir)$(OutDir)dist\fr\*.*\&quot; \&quot;$(TheProg)fr\&quot; ') -Verb RunAs&quot;" />

    <Message Importance="High" Text="&#xD;&#xA;    &#xD;&#xA;    ThePlugin Debug dlls copied to C:\Program Files\Thecorp\Theprog&#xD;&#xA;    &#xD;&#xA;&#xD;&#xA;" />

  </Target>




</Project>
```
