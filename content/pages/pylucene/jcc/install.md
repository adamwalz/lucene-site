Title: Install JCC
URL: pylucene/jcc/
save_as: pylucene/jcc/install.html
template: pylucene-jcc/page

##Getting JCC's Source Code

JCC's source code is included with PyLucene's. If you've downloaded
the PyLucene source code already, JCC's is to be found in
the <i>jcc</i> subdirectory.


To get the JCC source code only from SVN use:<br/>
<code>$ svn co
https://svn.apache.org/repos/asf/lucene/pylucene/trunk/jcc jcc</code>

##Building JCC

JCC is a Python extension written in Python and C++. It requires a
Java Runtime Environment to operate as it uses Java's reflection
APIs to do its work. It is built and installed
via <i>distutils</i>
or <a href="https://pypi.python.org/pypi/setuptools">setuptools</a>.


- On MacOS and Windows, <i>setup.py</i> will attempt to find a JDK on your
system and report what it found by showing the values for <i>JAVAHOME</i> and
<i>JAVAFRAMEWORKS</i> it was able to derive. If the JDK installation that was
found is not the one you wish to use or if you are not on MacOS or Windows,
you can either edit <i>setup.py</i> and review that the values in the
<i>INCLUDES</i>, <i>CFLAGS</i>, <i>DEBUG_CFLAGS</i>, <i>LFLAGS</i>,
<i>JAVAC</i>, and <i>JAVADOC</i> dicts are correct for your system or set
<b>all</b> of the environment variables <i>JCC_JDK</i>, <i>JCC_INCLUDES</i>,
<i>JCC_CFLAGS</i>, <i>JCC_DEBUG_CFLAGS</i>, <i>JCC_LFLAGS</i>,
<i>JCC_JAVAC</i> and <i>JCC_JAVADOC</i>, using os.pathsep as value separator
to override them.
The values hereby configured are going to be compiled into JCC's
<i>config.py</i> file and are going to be used by JCC when invoking
<i>setuptools</i> to compile the extensions it is used to generate code for.

- At the command line, enter:
<code>
$ python setup.py build<br/>
$ sudo python setup.py install<br/>
</code>


##Requirements

JCC requires a Java Development Kit to be present. It uses the Java
Native Invocation Interface and expects <i>&lt;jni.h&gt;</i>
and the Java libraries to be present at build and runtime.


JCC requires a C++ compiler. A recent C++ compiler for your
platform is expected to work as expected.


##Shared Mode: Support for the <i>--shared</i> Flag

JCC includes a small runtime that keeps track of the Java VM and of
Java objects escaping it. Because there can be only one Java VM
embedded in a given process at a time, the JCC runtime must be
compiled as a shared library when more than one JCC-built Python
extension is going to be imported into a given Python process.


Shared mode depends on <i>setuptools</i>' capability of
building plain shared libraries (as opposed to shared libraries for
Python extensions).


Currently, shared mode is supported with <i>setuptools 0.6c7</i> and above out
of the box on MacOS and Windows. On Linux, a patch to <i>setuptools</i> needs
to be applied first. This patch is included in the JCC source distribution in
the <i>jcc2/patches</i> directory, <i>patch.43</i>. This patch was submitted
to the <i>setuptools</i> project via <a
href="https://bugs.python.org/setuptools/issue43">issue 43</a>.
<i>setup.py</i> will attempt to apply the patch for you via monkeypatching.


The <i>shared mode disabled</i> error reported during the
build of JCC's on Linux contains the exact instructions on how to
patch the <i>setuptools</i> installation
with <i>patch.43</i> on your system.


Shared mode is also required when embedding Python in a Java VM as
JCC's runtime shared library is used by the JVM to load JCC and
bootstrap the Python VM via the JNI.


When shared mode is not enabled, not supported
or <i>distutils</i> is used instead
of <i>setuptools</i>, static mode is used instead. The JCC
runtime code is statically linked with each JCC-built Python
extension and only one such extension can be used in a given Python
process at a time.


As setuptools grows its shared library building capability it is
expected that more operating systems should be supported with shared
mode in the future.


Shared mode can be forced off by building JCC with
the <i>NO_SHARED</i> environment variable set.


There are two defaults to consider here:


- Is JCC built with shared mode support or not ?

    - By default, on MacOS, Linux or Windows, this is the case when using a
      modern version of <i>setuptools</i>

    - On other operating systems shared mode support is off by
      default - not supported - because shared mode depends on
      <i>setuptools</i>'s capability of building a regular
      shared library which is still an experimental feature.

- Is a JCC-built Python extension built with shared mode ?<br/>
    By default, no, shared mode is enabled only with
    the <i>--shared</i> command line argument.



##Notes for MacOS

On MacOS, Java is installed by Apple's setup as a framework. The
values in <i>setup.py</i> for <i>INCLUDES</i>
and <i>LFLAGS</i> for <i>darwin</i> should be correct
and ready to use when <i>setup.py</i> was able to derive <i>JAVAHOME</i> and
<i>JAVAFRAMEWORKS</i>.


  However, if you intend to use the 'system' Python from a Java VM
  on MacOS -- Python embedded in Java --
  you will need to add the flags <i>"-framework", "Python"</i>
  to the <i>LFLAGS</i> value.


##Notes for Linux

JCC has been built and tested on a variety of Linux distributions,
32- and 64-bit. Getting the java configuration correct is important
and is done differently for every distribution.<br/>
For example:


- On Ubuntu, to install Java 5, these commands may be used:
<code>
      $ sudo apt-get install sun-java5-jdk<br/>
      $ sudo update-java-alternatives -s java-1.5.0-sun<br/>
</code>
The samples flags for Linux in JCC's setup.py should be close to
correct.

- On Gentoo, the <i>java-config</i> utility should be used to
locate, and possibly change, the default java installation.
The sample flags for Linux in JCC's <i>setup.py</i> should
be changed to reflect the root of the Java installation which may
be obtained via:
<code>
      $ java-config -O
</code>



See earlier section about <a href="#shared">Shared Mode</a> for
Linux support.


##Notes for Solaris 11 with Sun Studio C++ 12

JCC has been built and tested on Solaris 11 with Sun Studio C++ 12, Java 1.6
and Python 2.4.


Because JCC is written in C++, Python's <i>distutils</i> must
be nudged a bit to invoke the correct compiler. Sun Studio's C
compiler is called <i>cc</i> while its C++ compiler is
called <i>CC</i>. To build JCC, use the following shell
command to ensure that the C++ compiler is used:

<code>
$ CC=CC python setup.py build
</code>

Shared mode is not currently implemented for
Solaris, <i>setuptools</i> needs to be taught how to build
plain shared libraries on Solaris first.


##Notes for Solaris 11.1 with GCC 4.5

JCC has been built and tested on Solaris 11.1 with gcc 4.5, Java 1.7 and
Python 2.6. Make sure, you?ve already installed the following packages:
gcc-4.5, jre-1.7, jdk-1.7, python-2.6, ant, gnu-make and subversion.

Missing packages can be installed via <i>pkg install</i>.

- Edit setup.py and do the following changes:
Inside JDK = { ? } change the entry for sunos5 to:
<code>'sunos5': '/usr/jdk/instances/jdk1.7.0',</code>
Inside CFLAGS= {?} change the entry for sunos5 to:
<code>'sunos5': ['-fno-strict-aliasing', '-Wno-write-strings'],</code>
- <code>python setup.py build</code>
- <code>su python setup.py install</code>


##Notes for Windows

At this time, JCC has been built and tested on Win2k and WinXP with
a variety of Python and Java versions.


- Adding the Python directory to <i>PATH</i> is recommended.

- Adding the Java directories containing the necessary DLLs and to
<i>PATH</i> is a must.

- Adding the directory containing <i>javac.exe</i>
to <i>PATH</i> is required for shared mode (enabled by
default if <i>setuptools >= 0.6c7</i> is found to be
installed).



##Notes for Python 2.3

To use JCC with Python 2.3, setuptools is required


- download <a href="https://pypi.python.org/pypi/setuptools">setuptools</a>.

- edit the downloaded <i>setuptools</i> egg file to use
python2.3 instead of python2.4.

- At the command line, run:<br/>
<code>$ sudo sh setuptools-0.6c7-py2.4.egg</code>
