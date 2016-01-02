##README for NetBSD

1. NetBSD 6 & 7 seems not have _SC_XOPEN_VERSION, defined it manually
    ```c
    #define _SC_XOPEN_VERSION 9
    ```
1. getenv_r is in stdlib.h,so comment it out

1. as far as cmsgcred(freebsd) is concernd, netbsd has sockcred.

1. AI_V4MAPPED and AI_ALL are not available on netbsd,comment it out.

1. netbsd doesn't support pthread_mutex_timedlock in pthread lib, we do not
build timedlock.c

1. define 2 macros(NETBSD and _NETBSD_SOURCE) in makefile to distinguish from other OSes and support
u_char

1. add a new Makefile.defines.netbsd file



## Origin README part
Read the file called DISCLAIMER.

On Freebsd and NetBSD, type "gmake".
On other platforms, type "make" (as long as this is gnu make).

For FAQs, updated source code, and the lost chapter, see http://www.apuebook.com.
Please direct questions, suggestions, and bug reports to sar@apuebook.com.

Steve Rago
January 2013

