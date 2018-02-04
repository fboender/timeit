TimeIt
======

A tiny python script that periodically runs a command and stores how long it
took to execute, the exit code and the output in a format convenient for
further processing in e.g. LibreOffice Calc.

## Usage

	usage: timeit [-h] [-i SECS] [-c TIMES] [-t CHARS] command

	positional arguments:
	  command

	optional arguments:
	  -h, --help            show this help message and exit
	  -i SECS, --interval SECS
	  -c TIMES, --count TIMES
	  -t CHARS, --trim-output CHARS

## Examples

Record ping response time every 5 seconds:

	$ timeit -i 5 'ping -w1 -c1 192.168.1.1 | grep "time=" | sed "s/.* time=\(.*\) ms$/\1/"'
	start_dt	start_ts	duration	exitcode	output
	2018-02-04 17:00:09	1517760009	0.006	0	3.74
	2018-02-04 17:00:14	1517760014	0.010	0	3.94
	2018-02-04 17:00:19	1517760019	0.011	0	3.99
	2018-02-04 17:00:24	1517760024	0.016	0	7.53

Record website response times every 10 seconds:

	$ ./timeit -i 10 'timeout 5 wget -O /dev/null https://www.electricmonk.nl 2> /dev/null'
	start_dt	start_ts	duration	exitcode	output
	2018-02-04 17:03:20	1517760200	0.254	0	
	2018-02-04 17:03:30	1517760210	0.292	0	
	2018-02-04 17:03:40	1517760220	0.293	0	
	2018-02-04 17:03:51	1517760231	0.278	0	
	2018-02-04 17:04:01	1517760241	0.231	0	
	2018-02-04 17:04:11	1517760251	0.229	0	
	
Example of running output through LibreOffice Calc's Charting feature:

![](https://raw.githubusercontent.com/fboender/timeit/master/oofice_chart.png)


## License

Released under the MIT license:

	Copyright 2017 Ferry Boender, released under the MIT license

    Permission is hereby granted, free of charge, to any person obtaining a
    copy of this software and associated documentation files (the "Software"),
    to deal in the Software without restriction, including without limitation
    the rights to use, copy, modify, merge, publish, distribute, sublicense,
    and/or sell copies of the Software, and to permit persons to whom the
    Software is furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in
    all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL
    THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
    FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
    DEALINGS IN THE SOFTWARE.

