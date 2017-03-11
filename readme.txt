DDMIN(1)                  BSD General Commands Manual                 DDMIN(1)

NAME
     ddmin — minimise textual test cases automatically

SYNOPSIS
     ddmin [-c] [-h] tester testfile

DESCRIPTION
     ddmin minimises testfile in place automatically using delta debugging.
     It works by by deleting lines (or characters with -c) while ensuring
     tester returns 0.

EXIT STATUS
     The ddmin utility exits 0 on success, and >0 if an error occurs.

EXAMPLE
     Given the input file test.c:

     #include <stdio.h>

     int main()
     {
             printf("hello world!");
             return 0;
     }

     The test script test.sh:

     #! /bin/sh

     set -e

     gcc test.c
     if ! ./a.out | grep -q "hello" then
             exit 1
     fi

     The invocation:

     ddmin -c ./test.sh ./test.c

     Produces the minimised output:

     main(){printf("hello");return;}

BSD                             March 11, 2017                             BSD
