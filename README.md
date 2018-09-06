tcalc
=====

Evaluate temporal arithmetic expressions, i.e. calculate time sums and differences.

A spontaneous hack at 11 p.m. with error handling to match.

Usage
-----

1. Run
2. Enter expression on stdin
3. Get result
4. Repeat
5. Enter an empty line (or EOF) to quit

Expression format, operators
----------------------------

Time formats:

* _"Time"_, e.g. `14:02`.
* _"Minute"_, e.g. `31`.

Operators (in decreasing order of precedence):

* `.` — calculate difference between two _times_.  
  `..`, `...`, etc are also valid.  
  If the second operand is smaller than the first, a midnight crossing is assumed and calculated.
* `+` and `-` — add / subtract.  
  Expect two operands. Each operand can be a _time_ or a _minute_.

Verbose mode:

* Append a `?` (or multiple) to an expression to enable verbose mode.  
  Verbose mode prints all intermediate values as they are calculated.

Examples
--------

    1
    0:01

    9:00..17:00
    8:00

    9:00..17:00-35
    7:25

    20:15+1:30
    21:45

    20:15+90
    21:45

    20:15+3:50
    24:05

    9:15..18:41-44+2:31+19
    11:32

    9:15..18:41-44+2:31+19?
    . 9:15 to 18:41 = 566 minutes (9:26)
    > 2:31 = 151 minutes (2:31)
    < 566 minutes = 566 total (9:26)
    - 44 minutes = 522 total (8:42)
    + 151 minutes = 673 total (11:13)
    + 19 minutes = 692 total (11:32)
    11:32
