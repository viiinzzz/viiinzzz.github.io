# Ciboulette blog

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

We are in year 2024. Cobol started in 1959.

This week I took the course "From Zero to **Cobol**" and rather found myself being a modern day archaeologist of early IT artefacts...

- Astonishingly, there are `.` going around, supposed to delimit blocks, the result is awkward, trying to show a start and an end with only one character. Clearly not enough, so there are plenty lot `End-XXX` stuff as well. Happily modern languages use braces, whichever they are `( ) or { }` they come in handy.
- Secondly, if you read the punch card story you understand, column 1 to 7 are reserved, over 72 are ignored... what the hell, nobody thought to upgrade the language a bit. nope. it's still in its original condition, pure vintage, I tell you.
- The data types are mostly fixed length, and mostly number in strings. It looks nice for statish-globalish-style programming ain't it?
- It's got the funny hierarchy numbers before the variable declaration, it's odd nonetheless it is working. That's the ancestor of the `struct` but a rather coarse one.
- Modularity, wait, just a method call, is at the expense of lengthy linkage contortion, don't even think of OOP, it's a parallel universe. It's called sub-programming. Wooow.

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


# Unit tests with CobolCheck


```Cobol
	  *SUT
	  *----------------------------------------------------------------
       IDENTIFICATION DIVISION.

       PROGRAM-ID.  C1959.

       ENVIRONMENT DIVISION.
       INPUT-OUTPUT SECTION.
       FILE-CONTROL.

       DATA DIVISION.
       WORKING-STORAGE SECTION.
       01  FILLER.
           05  birth           PIC 9(4).
           05  now             PIC 9(4).
           05  longevity       PIC 9(4).

       PROCEDURE DIVISION.
           GOBACK.
	  
	  *testResults
	  *----------------------------------------------------------------
```
  
   [test/C1959/C1959.cut]
```cobol
	  *TestSuite "Tests of Cobol longevity"

      *TestCase "Given Cobol was born in 1959,"
           MOVE 1959 to birth
      * Expect birth to be 1959

      *TestCase "  and that we're already in 2024,"
           MOVE 2024 to now
      * Expect now to equal 2024

      *TestCase "  it means Cobol has been around for 55 years !"
           SUBTRACT birth FROM now GIVING longevity
      * Expect longevity = 55
```
   
   [_cobolcheck/testResults.txt]
   ```text
TESTSUITE:
Tests of Cobol longevity
     PASS:   1. Given Cobol was born in 1959,
     PASS:   2.   and that we're already in 2024,
**** FAIL:   3.   it means Cobol has been around for 55 years !      
    EXPECTED +00000000055.0000000
         WAS +00000000065.0000000
 
  3 TEST CASES WERE EXECUTED
  2 PASSED
  1 FAILED
  0 CALLS NOT MOCKED
=================================================
```

❌ My mistake, not 55 but 65 years, let's correct expectation:

```cobol
      *TestCase "  it means Cobol has been around for 65 years !"
           SUBTRACT birth FROM now GIVING longevity
      * Expect longevity = 65
```

```
TESTSUITE:
Tests of Cobol longevity
     PASS:   1. Given Cobol was born in 1959,
     PASS:   2.   and that we're already in 2024,
     PASS:   3.   it means Cobol has been around for 65 years !
 
  3 TEST CASES WERE EXECUTED
  3 PASSED
  0 FAILED
  0 CALLS NOT MOCKED
=================================================
```

✔️ All passed

More to be explored:
https://github.com/openmainframeproject/cobol-check/wiki/How-to-guides

# File I/O

When using the regular `cobc` I had success reading file.
Badly my `cobc-sql` get tangled with when accessing files, so for this example make sure to use `cobc`.

```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. READCSV.

       ENVIRONMENT DIVISION.
       INPUT-OUTPUT SECTION.
       FILE-CONTROL.

           SELECT csv ASSIGN TO 'sample.csv'
               ORGANIZATION IS LINE SEQUENTIAL
               file status state.

       DATA DIVISION.
       FILE SECTION.
       FD  csv.

       1   row PIC X(255).

       WORKING-STORAGE SECTION.

       1   state pic 9(2) value zero.

       1   eof PIC X value 'N'.
        88  done value 'Y'.

       1   rowIndex pic 9(5) comp-5 value 0.
        88  isHeader value 00001.

       1   rowIndexStr redefines rowIndex pic ZZZZ9.

       1   customer.
        2   customerId PIC X(30) VALUE ALL ZERO.
         2   filler    PIC XX VALUE '| '.
        2   lastname   PIC X(30) VALUE ALL ZERO.
         2   filler    PIC XX VALUE '| '.
        2   firstname  PIC X(30) VALUE ALL ZERO.
         2   filler    PIC XX VALUE '| '.
        2   balance    PIC X(30) VALUE ALL ZERO.

       1   customerSepa.
        2   customerIdSepa PIC X(30) VALUE ALL '-'.
         2   filler        PIC XX VALUE '+-'.
        2   lastnameSepa   PIC X(30) VALUE ALL '-'.
         2   filler        PIC XX VALUE '+-'.
        2   firstnameSepa  PIC X(30) VALUE ALL '-'.
         2   filler        PIC XX VALUE '+-'.
        2   balanceSepa    PIC X(30) VALUE ALL '-'.

       1   customersArrayLen PIC 9(5) COMP-5 VALUE 1.

       1   customersArray.
        2   customers    OCCURS 1 TO 1000 TIMES
                         DEPENDING ON customersArrayLen
                         INDEXED BY i.
         3   vcustomerId PIC X(30) VALUE ALL ZERO.
         3   vlastname   PIC X(30) VALUE ALL ZERO.
         3   vfirstname  PIC X(30) VALUE ALL ZERO.
         3   vbalance    PIC X(30) VALUE ALL ZERO.
         
       1   userName PIC X(255).

       PROCEDURE DIVISION.

           DISPLAY "USERNAME" UPON ENVIRONMENT-NAME.
           ACCEPT userName FROM ENVIRONMENT-VALUE.
           DISPLAY "Hello " userName

           INITIALIZE customersArray

           OPEN INPUT csv
              if state not = '00'
                 display 'read error: ' state
                 if state = '35'
                    display '(file not found)'
                 end-if
                 goback
              end-if

              PERFORM UNTIL done

                 READ csv

                 AT END
                    SET done TO TRUE

                 NOT AT END
                     PERFORM readRow
                     PERFORM printRow
                     PERFORM storeRow

                 END-READ

              END-PERFORM CLOSE csv

              display 'array='
              display customersArray
           goback.


       readRow.

           ADD 1 TO rowIndex
           INITIALIZE customer

           UNSTRING row DELIMITED BY ','
              INTO customerId lastname firstname balance
           .

  
       printRow.

           DISPLAY customer

           IF isHeader
              DISPLAY customerSepa
           END-IF
           .

  
       storeRow.

           if NOT isHeader
              ADD 1 TO customersArrayLen
              SET i to rowIndex.

              MOVE customerId  TO vcustomerId(i)
              MOVE lastname TO vlastname(i)
              MOVE firstname TO vfirstname(i)
              MOVE balance TO vbalance(i)
           .
```

```text
Hello buddy                                                                                                                                                     

id                            | lastname                      | firstname                     | balance
------------------------------+-------------------------------+-------------------------------+-------------------------------
920751                        | trump                         | donald                        | 100000000
593102                        | harris                        | kamala                        | 10000000
3463110                       | cobol                         | developer                     | 10000
array=
id                            lastname                      firstname                     balance                       920751                        trump                         donald                        100000000                     593102                        harris                        kamala              
          10000000                      3463110                       cobol                         developer                     10000

```

# Sub programming

Again, rather use the regular `cobc` because the sub will need the -m switch which is not available (yet.)

So what is it about: _in C# it would be
_
```c#
public static class Sub {
	public static Ret Work(this User user) { ... }
}

//to be called from a

public static class Parent {
	public static void Work() {
		var toto = new User(...);
		var result = Sub.Work(toto);
	}
}
```

```
[parent.cob] `cobc -x parent.cob`
```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. parent.

       ENVIRONMENT DIVISION.
       DATA DIVISION.
       WORKING-STORAGE SECTION.

       1   sub pic X(8).

       1   sub-dothat pic X(8).

       1   user.
        2   lastname pic X(12).
        2   firstname pic X(12).

       1   location.
        2   street pic X(30).
        2   town pic X(15).
        2   zipcode pic 9(5).

       1   ret.
        2   err.
         3   errcode pic 999.
         3   errmsg pic X(255).
        2   blob.
         3   datlen  PIC S9(9) COMP-5.
         3   dat    PIC X(1024).

       PROCEDURE DIVISION.

           DISPLAY '---PARENT RISE'

           MOVE 'sub' TO sub.
           MOVE 'dothat' TO sub-dothat.

           INITIALIZE user.
           INITIALIZE location.
           INITIALIZE ret.

           move 'new' to lastname.
           move 'bie' to firstname.
           move '1 orchard road' to street.
           move 'armonk' to town.
           move 10504 to zipcode.

           DISPLAY
              '   I AM PARENT AND I GIVE'
           DISPLAY
              '      user='
           DISPLAY
              user
           DISPLAY
              '  AND location='
           DISPLAY
              location
           DISPLAY
              '      TO SUB'

           call sub using ret
                    by content user, by content location.

      *    cancel sub.

           DISPLAY ' '
           DISPLAY
              '---PARENT I'M BACK
           DISPLAY
              '   ret='
              ret

           move 'cobol' to lastname.
           move 'dev' to firstname.

           DISPLAY ' '
           DISPLAY
              '   I AM PARENT AND I GIVE'
           DISPLAY
              '      user='
           DISPLAY
              user
           DISPLAY
              '      TO SUB/DOTHAT'

           INITIALIZE ret.

           call sub-dothat using ret
                    by content user, by content location.

           DISPLAY ' '
           DISPLAY '---PARENT I''M BACK
           DISPLAY '---PARENT SUNSET'

           stop run.
```

[sub.cob] `cobc -m sub.cob`
```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. sub.

       ENVIRONMENT DIVISION.
       DATA DIVISION.
       LINKAGE SECTION.

       1   user.
        2   lastname pic X(12) value LOW-VALUES.
        2   firstname pic X(12) value LOW-VALUES.
       1   location.
          2 street   pic X(30) VALUE LOW-VALUES.
          2 town   pic X(15) VALUE LOW-VALUES.
          2 zipcode   pic 9(5) VALUE LOW-VALUES.

       1   ret.
        2   err.
         3   errcode pic 999 VALUE LOW-VALUES.
         3   errmsg pic X(255) VALUE LOW-VALUES.
        2   blob.
         3   datlen  PIC S9(9) COMP-5 VALUE LOW-VALUES.
         3   dat    PIC X(1024) VALUE LOW-VALUES.

       PROCEDURE DIVISION USING ret, user, location.

           DISPLAY ' '
           DISPLAY '   ---SUB RISE'

      *    dummy processing

           move 000 to errcode.
           move 10 to datlen.
           move 'ABCDEFGHIJ' to dat.

           DISPLAY
              '      I AM SUB AND I GOT'
           DISPLAY
              '         user='
           DISPLAY
              user
           DISPLAY
              '     AND location='
           DISPLAY
              location
           DISPLAY
              '         FROM PARENT'
           DISPLAY
              '   ---SUB SUNSET I RETURN'
           DISPLAY
              '         ret='
           DISPLAY
              ret
           DISPLAY
              '         TO PARENT'

           EXIT PROGRAM.

  
           ENTRY 'dothat' using ret, user, location.

               DISPLAY
                  ' '
               DISPLAY
                  '   ---SUB DO THAT RISE'
               DISPLAY
                  '      I AM SUB AND I GOT'
               DISPLAY
                  '         user='
               DISPLAY
                  user
                  
               DISPLAY
                  '   ---SUB DO THAT SUNSET'

               GOBACK.
```

```txt
---PARENT RISE
   I AM PARENT AND I GIVE
      user=
new         bie
  AND location=
1 orchard road                armonk         10504
      TO SUB
 
   ---SUB RISE
      I AM SUB AND I GOT
         user=
new         bie
     AND location=
1 orchard road                armonk         10504
         FROM PARENT
   ---SUB SUNSET I RETURN
         ret=
000                                                                                                                                                              

ABCDEFGHIJ                                                                                                                                                       
                                                                                                                                                                 
                                                                                                                                                                 
                                                                                                                                                                 
                                                                                                                                                                 
                                                                                                                                                                 

         TO PARENT

---PARENT I'M BACK
   ret=000                                                                                                                                                       

ABCDEFGHIJ                                                                                                                                                       
                                                                                                                                                                 
                                                                                                                                                                 
                                                                                                                                                                 
                                                                                                                                                                 
                                                                                                                                                                 


   I AM PARENT AND I GIVE
      user=
cobol       dev
      TO SUB/DOTHAT

   ---SUB DO THAT RISE
      I AM SUB AND I GOT
         user=
cobol       dev
   ---SUB DO THAT SUNSET

---PARENT I'M BACK
---PARENT SUNSET
```


