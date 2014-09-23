NCSA - Parses ncsa logs with ease!

Here is some help!

```
bash-3.2$ ncsa -h
  -h Print this help
  -s Sort by number of requests
  -S Breakdown to the second
  -M Breakdown to the minute
  -H Breakdown to the hour
  -p Dont print percentage, instead print count of requests
  -v Be verbose and print actual request information
```

Dump ncsa log and break requests per hour.

```
utopia:ncsa kazu$ cat  nginx.log | ncsa -H
2014 Sep 23 06      88 requests    0.00 (%) -
2014 Sep 23 07    2508 requests    6.00 (%) - ||||||
2014 Sep 23 08    2922 requests    8.00 (%) - ||||||||
2014 Sep 23 09    1817 requests    5.00 (%) - |||||
2014 Sep 23 10    1898 requests    5.00 (%) - |||||
2014 Sep 23 11    2725 requests    7.00 (%) - |||||||
2014 Sep 23 12    2023 requests    5.00 (%) - |||||
2014 Sep 23 13    2084 requests    5.00 (%) - |||||
2014 Sep 23 14    2344 requests    6.00 (%) - ||||||
2014 Sep 23 15    2415 requests    6.00 (%) - ||||||
2014 Sep 23 16    1642 requests    4.00 (%) - ||||
2014 Sep 23 17    2269 requests    6.00 (%) - ||||||
2014 Sep 23 18    2826 requests    7.00 (%) - |||||||
2014 Sep 23 19    3927 requests   10.00 (%) - ||||||||||
2014 Sep 23 20    2482 requests    6.00 (%) - ||||||
2014 Sep 23 21    1650 requests    4.00 (%) - ||||
2014 Sep 23 22     241 requests    0.00 (%) -
```

Dump ncsa log and break requests per hour and sort!.

```
utopia:ncsa kazu$ cat  nginx.log | ncsa -H -s
2014 Sep 23 06      88 requests    0.00 (%) -
2014 Sep 23 22     241 requests    0.00 (%) -
2014 Sep 23 16    1642 requests    4.00 (%) - ||||
2014 Sep 23 21    1650 requests    4.00 (%) - ||||
2014 Sep 23 09    1817 requests    5.00 (%) - |||||
2014 Sep 23 10    1898 requests    5.00 (%) - |||||
2014 Sep 23 12    2023 requests    5.00 (%) - |||||
2014 Sep 23 13    2084 requests    5.00 (%) - |||||
2014 Sep 23 17    2269 requests    6.00 (%) - ||||||
2014 Sep 23 14    2344 requests    6.00 (%) - ||||||
2014 Sep 23 15    2415 requests    6.00 (%) - ||||||
2014 Sep 23 20    2482 requests    6.00 (%) - ||||||
2014 Sep 23 07    2508 requests    6.00 (%) - ||||||
2014 Sep 23 11    2725 requests    7.00 (%) - |||||||
2014 Sep 23 18    2826 requests    7.00 (%) - |||||||
2014 Sep 23 08    2922 requests    8.00 (%) - ||||||||
2014 Sep 23 19    3927 requests   10.00 (%) - ||||||||||
```

Grab just a frew requests and dump a breakdown per second!

```
utopia:ncsa kazu$ tail nginx.log | ncsa -S
2014 Sep 23 22:11:04       1 requests   10.00 (%) - ||||||||||
2014 Sep 23 22:11:05       1 requests   10.00 (%) - ||||||||||
2014 Sep 23 22:11:08       1 requests   10.00 (%) - ||||||||||
2014 Sep 23 22:11:09       3 requests   30.00 (%) - ||||||||||||||||||||||||||||||
2014 Sep 23 22:11:10       2 requests   20.00 (%) - ||||||||||||||||||||
2014 Sep 23 22:11:13       1 requests   10.00 (%) - ||||||||||
2014 Sep 23 22:11:24       1 requests   10.00 (%) - ||||||||||
```

Grab just a frew requests and dump a breakdown per second and sort!

```
utopia:ncsa kazu$ tail nginx.log | ncsa -S -s
2014 Sep 23 22:11:13       1 requests   10.00 (%) - ||||||||||
2014 Sep 23 22:11:05       1 requests   10.00 (%) - ||||||||||
2014 Sep 23 22:11:24       1 requests   10.00 (%) - ||||||||||
2014 Sep 23 22:11:08       1 requests   10.00 (%) - ||||||||||
2014 Sep 23 22:11:04       1 requests   10.00 (%) - ||||||||||
2014 Sep 23 22:11:10       2 requests   20.00 (%) - ||||||||||||||||||||
2014 Sep 23 22:11:09       3 requests   30.00 (%) - ||||||||||||||||||||||||||||||
```

Grab just a frew requests and dump a breakdown per second and sort but print a bar (|) per request instead of showing a percentage breakdown!

```
utopia:ncsa kazu$ tail nginx.log | ncsa -S -s -p
2014 Sep 23 22:11:04       1 requests   10.00 (#) - |
2014 Sep 23 22:11:08       1 requests   10.00 (#) - |
2014 Sep 23 22:11:05       1 requests   10.00 (#) - |
2014 Sep 23 22:11:13       1 requests   10.00 (#) - |
2014 Sep 23 22:11:24       1 requests   10.00 (#) - |
2014 Sep 23 22:11:10       2 requests   20.00 (#) - ||
2014 Sep 23 22:11:09       3 requests   30.00 (#) - |||
```

