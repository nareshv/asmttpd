asmttpd
=======

Web server for Linux written in amd64 assembly.

Note: This is very much a work in progress and not ready for production.

Features:
* Multi-threaded via a thread pool
* No libraries required ( only 64-bit Linux )
* Fast

What works:
* Serving files from specified document root.
* 200
* 206 
* 404 
* Content-types: xml, html, xhtml, gif, png, jpeg, css, js, and octet-stream.
  
Planned Features:
* Directory listing.
* HEAD support.

Current Limitations / Known Issues
=======
* 206 Partial Content body is limited to ~10MB, make another request to continue.
* Implementation of proper HTTP error codes.

Installation
=======

Run make or make release for non-debug version.

You will need yasm installed.

Usage
=======

./asmttpd /path/to/web_root

Changes
=======
2014-02-03 : asmttpd - 0.04

* 200 now streams full amount


2014-02-01 : asmttpd - 0.03

* Files are split if too large to fit into buffer. 
* Added 206 responses with Content-Range handling


2014-01-30 : asmttpd - 0.02

* Added xml, xhtml, gif, png, jpeg, css, and javascript content types.
* Changed thread memory size to something reasonable. You can tweak it according to available memory. See comments in main.asm
* Added simple request logging.
* Added removal of '../' in URL.
