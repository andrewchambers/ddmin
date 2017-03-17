DDMIN(1)                  BSD General Commands Manual                 DDMIN(1)

NAME
     ddmin — minimise interesting files automatically

SYNOPSIS
     ddmin [-b] [-h] tester interesting

DESCRIPTION
     ddmin minimises file interesting in place automatically using delta
     debugging.  It works by by deleting lines (or bytes with -b) while ensur‐
     ing tester returns 0 when executed.

EXIT STATUS
     The ddmin utility exits 0 on success, and >0 if an error occurs.

EXAMPLE
     Given the input file interesting.c:

     #include <stdio.h>

     int main()
     {
             printf("hello world!");
             return 0;
     }

     The test script test.sh:

     #! /bin/sh

     set -e

     gcc interesting.c
     if ! ./a.out | grep -q "hello" then
             exit 1
     fi

     The invocation:

     ddmin -b ./test.sh ./interesting.c

     Produces the minimised output:

     main(){printf("hello");return;}

BSD                              March 8, 2017                             BSD
