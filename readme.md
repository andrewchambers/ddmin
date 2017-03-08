Content-type: text/html; charset=UTF-8

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<HTML><HEAD><TITLE>
Man page of DDMIN
</TITLE>
</HEAD><BODY>
<H1>
DDMIN
</H1>
Section: User Commands (1)<BR><A HREF="#index">Index</A>
<A HREF="/cgi-bin/man/man2html">Return to Main Contents</A>
<HR>
<BR>BSD mandoc<BR> <A NAME="lbAB"> </A>
<H2>
NAME
</H2>



<B>ddmin</B>

-   minimise textual test cases automatically

<A NAME="lbAC"> </A>
<H2>
SYNOPSIS
</H2>

<B>ddmin</B>

[-<B>c</B>

]

[-<B>h</B>

]

<I>tester</I>

<I>testfile</I>

<A NAME="lbAD"> </A>
<H2>
DESCRIPTION
</H2>

<B>ddmin</B>

minimises <I>testfile</I>

in place automatically using delta debugging. It works by by deleting
lines (or characters with -c) while ensuring <I>tester</I>

returns 0. <A NAME="lbAE"> </A>
<H2>
EXIT STATUS
</H2>

Ex -std ddmin

<A NAME="lbAF"> </A>
<H2>
EXAMPLE
</H2>


<PRE>
Given the input file test.c:

#include &lt;<A HREF="file:///usr/include/stdio.h">stdio.h</A>&gt;

int main()
{
        printf(&quot;hello world!);
        return 0;
}

The test script test.sh:

#! /bin/sh

set -e

gcc test.c
if ! ./a.out | grep -q &quot;hello&quot; then
        exit 1
fi

The invocation:

ddmin -c ./test.sh ./test.c

Produces the minimised output:

int main(){printf(&quot;hello&quot;);return;}
</pre>


<HR>
<A NAME="index"> </A>
<H2>
Index
</H2>
<DL>
<DT>
<A HREF="#lbAB">NAME</A>
<DD>
<DT>
<A HREF="#lbAC">SYNOPSIS</A>
<DD>
<DT>
<A HREF="#lbAD">DESCRIPTION</A>
<DD>
<DT>
<A HREF="#lbAE">EXIT STATUS</A>
<DD>
<DT>
<A HREF="#lbAF">EXAMPLE</A>
<DD>
</DL>
<HR>
This document was created by
<A HREF="/cgi-bin/man/man2html">man2html</A>, using the manual
pages.<BR> Time: 12:00:17 GMT, March 08, 2017
</BODY>
</HTML>



