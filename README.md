## On the maintainer’s system:

```
aclocal # for init m4 env
autoconf # To gen configure from configure.ac
automake --add-missing # To gen Makefile.in from Makefile.am
./configure # To gen Makefile from Makefile.in
make distcheck # Makefile to build (Will also release tarball to distribute)
```

## On the end-user’s system:

```
./configure # To gen Makefile from Makefile.in
make # Makefile to build the program
make install # Makefile to install the program  (If you're getting an [* install-am] Error 2 or pocess exited or 
terminated with Error 2, make sure you've W permissions on /usr/local/bin or /usr/bin) Running with sudo will solve it)
```


## Explanation 

1) configure
``` configure ```  script is responsible for getting ready to build the software on your specific system. It makes sure all of 
the dependencies are available and checks whatever it needs to know 
to use those dependencies.

2) make
Build the software using make
This runs a series of tasks defined in a Makefile to build the finished program from its source code.

The tarball doesn’t include a finished Makefile. Instead it comes with a template called Makefile.in
and the configure script produces a customised Makefile specific to your system.

3) make install
The make install command will copy the built program, and its libraries and documentation, to the correct location.


## Quick-explanation build process

```configure.ac``` contains m4 macros which describes what configur script needs to do.

```Makefile.am``` is a programmer-defined file and is used by automake to generate the Makefile.in file (the .am stands for 
automake). The configure script typically seen in source tarballs will use the Makefile.in to generate a Makefile.

imp macros in Makefile.am 
```AUTOMAKE_OPTIONS = foreign``` Means that we'ree not gonna use the GNU's standard layout. so don't warn about the non-std fmt

```bin_PROGRAMS = helloworld``` Specifies what out programs binary should be. like exe in windows.

```helloworld_SOURCES = main.c``` Telling automake where to find the src files.



