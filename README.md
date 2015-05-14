GWT Example
===========

Example to show how to use GWT SuperDevMode + Maven + Eclipse for debugging.  Firstly import into Eclipse with File > Import > Existing Maven projects.

Setup
-----

Now you have to compile it at least once by either:

* Right-clicking on the project then Google > GWT Compile.  For some reason this does not automatically recognise where to compile the webapp to, so you need to select it manually.  There's probably a way around this, but sod it, I'm fed up of trying things and this works anyway.
* From the command-line running `mvn gwt:compile`

You now have two options to start things up properly.  The easy one is:

* Right-click the project
* Run As > Web Application (GWT Super Dev Mode)

That will start 2 things - a local server on 127.0.0.1:8888 which will run the webapp, and the code server needed to run super dev mode, for debugging etc.

The slightly more involved (but better IMO) way is this:

* Right-click the project
* Run As > Run on server
* Configure as per usual for running a webapp on the server

So now you have the webapp running on your usual servlet container (Tomcat in my case) and you can debug all the server stuff as usual.  However, to run the code server, you need to create a *Java* application launcher (i.e. not a GWT one or a server one) with the main class as:

com.google.gwt.dev.codeserver.CodeServer

and with program arguments set to:

-src src/main/java -port 9876 uk.ac.rdg.resc.gwtexample.web.GWTExample

Debugging
---------

This seems to work in Chrome, so use that.

If you don't already have the "Dev Mode On" and "Dev Mode Off" links, on the bookmark toolbar (Ctrl+Shift+B if it's not there), go to localhost:9876 (or whatever the port you specified in the code server was) and follow the instructions.

Now visit the page running on the server.  For the easy method this will be at http://127.0.0.1:8888/index.html, if it's running on Tomcat it'll be http://localhost:8080/gwt-example/index.html

Open the developer tools (Ctrl+Shift+I) and go to the "Sources" tab.  You should be able to see the Java source code under localhost:9876 > sourcemaps/gwtexample/uk/ac/rdg/...

You can then add breakpoints, step through code, see variable values etc...

Notes
-----

* This is all written during experimentation, and may or may not be added to.
* You can edit Java directly in Chrome, but you need to add the files to the (Chrome) workspace to do so.  I haven't played with that yet, but you can just edit code in Eclipse.

