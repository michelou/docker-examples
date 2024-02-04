# <span id="top">Playing with Docker on Windows</span>

<table style="font-family:Helvetica,Arial;line-height:1.6;">
  <tr>
  <td style="border:0;padding:0 10px 0 0;min-width:100px;"><a href="https://www.docker.com/" rel="external"><img style="border:0;" src="./docs/images/moby.png" width="100" alt="Docker project"/></a></td>
  <td style="border:0;padding:0;vertical-align:text-top;">This repository gathers <a href="https://www.docker.com/" rel="external">Docker</a> code examples coming from various websites and books.<br/>
  It also includes several <a href="https://en.wikibooks.org/wiki/Windows_Batch_Scripting" rel="external">batch files</a> for experimenting with <a href="https://www.docker.com/" rel="external">Docker</a> on the Windows machine.
  </td>
  </tr>
</table>

[Ada][ada_examples], [Akka][akka_examples], [C++][cpp_examples], [Dart][dart_examples], [Deno][deno_examples], [Flix][flix_examples], [Golang][golang_examples], [GraalVM][graalvm_examples], [Haskell][haskell_examples], [Kafka][kafka_examples], [Kotlin][kotlin_examples], [LLVM][llvm_examples], [Modula-2][m2_examples], [Node.js][nodejs_examples], [Rust][rust_examples], [Scala 3][scala3_examples], [Spark][spark_examples], [Spring][spring_examples], [TruffleSqueak][trufflesqueak_examples] and [WiX Toolset][wix_examples] are other trending topics we are continuously monitoring.

## <span id="proj_deps">Project dependencies</span> [**&#x25B4;**](#top)

- [Docker Desktop 4.27][docker_downloads] ([*release notes*][docker_relnotes])
- [Git 2.43][git_downloads] ([*release notes*][git_relnotes])

Optionally one may also install the following software:

- [Visual Studio Code 1.86][vscode_downloads] ([*release notes*][vscode_relnotes])

> **:mag_right:** [Git for Windows][git_downloads] provides a BASH emulation used to run [**`git`**][git_docs] from the command line (as well as over 250 Unix commands like [**`awk`**][man1_awk], [**`diff`**][man1_diff], [**`file`**][man1_file], [**`grep`**][man1_grep], [**`more`**][man1_more], [**`mv`**][man1_mv], [**`rmdir`**][man1_rmdir], [**`sed`**][man1_sed] and [**`wc`**][man1_wc]).
For instance our development environment looks as follows (February 2024) <sup id="anchor_01">[1](#footnote_01)</sup>:

<pre style="font-size:80%;">
C:\opt\Git\                <i>(366 MB)</i>
C:\opt\VSCode\             <i>(341 MB)</i>
C:\Program Files\Docker\   <i>(2.8 GB)</i>
</pre>

## <span id="structure">Directory structure</span> [**&#x25B4;**](#top)

This project is organized as follows:
<pre style="font-size:80%;">
<a href="bin/">bin\</a>
<a href="docs/">docs\</a>
<a href="examples/">examples\</a>{<a href="examples/README.md">README.md</a>}
README.md
<a href="RESOURCES.md">RESOURCES.md</a>
<a href="setenv.bat">setenv.bat</a>
</pre>

where

- directory [**`bin\`**](bin/) provides several utility [batch files][windows_batch_file].
- directory [**`docs\`**](docs/) contains [Docker] related papers/articles.
- directory [**`examples\`**](examples/) contains [Docker] code examples grabbed from various websites.
- file [**`README.md`**](README.md) is the [Markdown][github_markdown] document for this page.
- file [**`RESOURCES.md`**](RESOURCES.md) gathers [Docker] related informations.
- file [**`setenv.bat`**](setenv.bat) is the batch script for setting up our environment.

We also define a virtual drive &ndash; e.g. drive **`O:`** &ndash; in our working environment in order to reduce/hide the real path of our project directory (see article ["Windows command prompt limitation"][windows_limitation] from Microsoft Support).

> **:mag_right:** We use the Windows external command [**`subst`**][windows_subst] to create virtual drives; for instance:
>
> <pre style="font-size:80%;">
> <b>&gt; <a href="https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/subst">subst</a> O: <a href="https://en.wikipedia.org/wiki/Environment_variable#Default_values">%USERPROFILE%</a>\workspace\docker-examples</b>
> </pre>

In the next section we give a brief description of the batch files present in this project.

## <span id="commands">Batch commands</span> [**&#x25B4;**](#top)

### [**`setenv.bat`**](setenv.bat)

We execute command [**`setenv.bat`**](setenv.bat) once to setup our development environment; it makes external tools such as [**`docker.exe`**][docker_cli], [**`git.exe`**][git_cli], and [**`sh.exe`**][sh_cli] directly available from the command prompt.

<pre style="font-size:80%;">
<b>&gt; <a href="setenv.bat">setenv</a> -verbose</b>
Tool versions:
   docker 25.0.2,
   git 2.43.0.windows.1, diff 3.10, bash 5.2.21(1)-release
Tool paths:
   C:\Program Files\Docker\Docker\resources\bin\docker.exe
   C:\opt\Git\bin\git.exe
   C:\opt\Git\usr\bin\diff.exe
   C:\opt\Git\bin\bash.exe
Environment variables:
   "DOCKER_HOME=C:\Program Files\Docker\Docker\"
   "GIT_HOME=C:\opt\Git"
Path associations:
   O:\: => C:\Users\michelou\workspace-perso\docker-examples\

<b>&gt; <a href="https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/where_1" rel="external">where</a> docker git sh</b>
C:\Program Files\Docker\Docker\resources\bin\docker
C:\Program Files\Docker\Docker\resources\bin\docker.exe
C:\opt\deno\deno.exe
C:\opt\Git\bin\git.exe
C:\opt\Git\mingw64\bin\git.exe
C:\opt\Git\bin\sh.exe
C:\opt\Git\usr\bin\sh.exe
</pre>

## <span id="footnotes">Footnotes</span>

<span id="footnote_01">[1]</span> ***Downloads*** [↩](#anchor_01)

<dl><dd>
In our case we downloaded the following installation files (see <a href="#proj_deps">section 1</a>):
</dd>
<dd>
<pre style="font-size:80%;">
<a href="">Docker Desktop Installer.exe</a>      <i>(481 MB)</i>
<a href="https://git-scm.com/download/win">PortableGit-2.43.0-64-bit.7z.exe</a>  <i>( 41 MB)</i>
</pre>
</dd></dl>

***

*[mics](https://lampwww.epfl.ch/~michelou/)/February 2024* [**&#9650;**](#top)  <!-- May 2022 -->
<span id="bottom">&nbsp;</span>

<!-- link refs -->

[ada_examples]: https://github.com/michelou/ada-examples
[akka_examples]: https://github.com/michelou/akka-examples
[book_portela]: https://www.packtpub.com/product/deno-web-development/9781800205666
[cpp_examples]: https://github.com/michelou/cpp-examples
[dart_examples]: https://github.com/michelou/dart-examples
[deno_examples]: https://github.com/michelou/deno-examples
[docker]: https://www.docker.com/
[docker_cli]: https://docs.docker.com/engine/reference/commandline/cli/
[docker_downloads]: https://docs.docker.com/desktop/windows/install/
[docker_relnotes]: https://docs.docker.com/desktop/windows/release-notes/
[flix_examples]: https://github.com/michelou/flix-examples
[git_cli]: https://git-scm.com/docs/git
[git_docs]: https://git-scm.com/docs/git
[git_downloads]: https://git-scm.com/download/win
[git_relnotes]: https://raw.githubusercontent.com/git/git/master/Documentation/RelNotes/2.43.0.txt
[github_markdown]: https://github.github.com/gfm/
[golang_examples]: https://github.com/michelou/golang-examples
[graalvm_examples]: https://github.com/michelou/graalvm-examples
[haskell_examples]: https://github.com/michelou/haskell-examples
[kafka_examples]: https://github.com/michelou/kafka-examples
[kotlin_examples]: https://github.com/michelou/kotlin-examples
[linux_opt]: https://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html
[llvm_examples]: https://github.com/michelou/llvm-examples
[m2_examples]: https://github.com/michelou/m2-examples
[man1_awk]: https://www.linux.org/docs/man1/awk.html
[man1_diff]: https://www.linux.org/docs/man1/diff.html
[man1_file]: https://www.linux.org/docs/man1/file.html
[man1_grep]: https://www.linux.org/docs/man1/grep.html
[man1_more]: https://www.linux.org/docs/man1/more.html
[man1_mv]: https://www.linux.org/docs/man1/mv.html
[man1_rmdir]: https://www.linux.org/docs/man1/rmdir.html
[man1_sed]: https://www.linux.org/docs/man1/sed.html
[man1_wc]: https://www.linux.org/docs/man1/wc.html
[nodejs_examples]: https://github.com/michelou/nodejs-examples
[rust_examples]: https://github.com/michelou/rust-examples
[scala3_examples]: https://github.com/michelou/dotty-examples
[sh_cli]: https://man7.org/linux/man-pages/man1/sh.1p.html
[spark_examples]: https://github.com/michelou/spark-examples
[spring_examples]: https://github.com/michelou/spring-examples
[trufflesqueak_examples]: https://github.com/michelou/trufflesqueak-examples
[vscode_downloads]: https://code.visualstudio.com/#alt-downloads
[vscode_relnotes]: https://code.visualstudio.com/updates/
[windows_batch_file]: https://en.wikibooks.org/wiki/Windows_Batch_Scripting
[windows_limitation]: https://support.microsoft.com/en-gb/help/830473/command-prompt-cmd-exe-command-line-string-limitation
[windows_subst]: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/subst
[wix_examples]: https://github.com/michelou/wix-examples
[zip_archive]: https://www.howtogeek.com/178146/htg-explains-everything-you-need-to-know-about-zipped-files/
