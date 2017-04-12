DDMIN(1) - General Commands Manual

# NAME

**ddmin** - minimise interesting files automatically

# SYNOPSIS

**ddmin**
\[**-b**]
\[**-h**]
*tester*
*interesting*

# DESCRIPTION

**ddmin**
minimises file
*interesting*
in place using delta debugging.
It works by deleting lines (or bytes with -b) while ensuring
*tester*
returns 0 when executed.

**ddmin**
forwards the stdout and stderr of successive
*tester*
executions to enable debug logging.

# EXIT STATUS

The **ddmin** utility exits&#160;0 on success, and&#160;&gt;0 if an error occurs.

# EXAMPLE

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

OpenBSD 6.1 - March 8, 2017
