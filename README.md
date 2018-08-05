Xdos tool
=============

XDOS tool ported to Go language from Python.
Original Python utility by itsR03D17w7
I just ported the code as is quick and dirty. Original functions names are keeped and original logic mostly keeped too.

The main difference from Python version layed in Golang architecture for concurrency: the goroutines. xdos.py runs
a new thread for each connection in the connection pool so it uses hundreds and thousands of threads.
xdos.go just uses lightweight goroutines that used only tens of threads (commonly golang runtime started one thread for
CPU core + several service threads). This architecture allows golang version better consume resources and got much higher
connection pool on the same hardware than Python version can.

This tool targeted for stress testing and may really down badly configured server or badly made app. Use it carefully.

Examples:

    $ xdos -site http://example.com/test/ 2>/dev/null

    $ XDOSMAXPROCS=4096 xdos -site http://example.com 2>/tmp/errlog

Useful environment vars:

* GOMAXPROCS
  Set it to number of your CPUs or higher (no more actual for latest golang versions).
* XDOSMAXPROCS
  Limit the connection pool (1024 by default).                                   

License
=======

I think it may be public domain because of it is just simple and short piece of code but for reason I don't remember already
I have choose GPL for it. Okey. So, Go version of XDOS licensed under GPLv3. See LICENSE.

I am not related with original XDOS utility in Python. Original XDOS utility is authority of itsR03D17w7. There are no                                    