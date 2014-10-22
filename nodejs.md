#Introduction

Node.js is a platform designed for easily creating fast, scalable network applications.

This guide will cover how to install and configure Node.js, as well as how to test it with a small and simple HTTP server.

#Installation

1. Connect to your slot through [SSH](/wiki/SSH)

2. Create the installation directory for Node.js

        mkdir ~/.config/nodejs
        
3. Download the source
 
        wget http://nodejs.org/dist/v0.10.32/node-v0.10.32.tar.gz

4. Extract the source and enter the directory

        tar -zxf node-v0.10.32.tar.gz; cd node-v0.10.32
        
5. Configure the installation. Ensure that the prefix option matches the location where we created the installation directory.

        ./configure --prefix=$HOME/.config/nodejs
        
6. Compile and install the source. (This step takes a while to execute. Be patient.)

        make; make install
        
8. Add the following line to ``~/.bashrc`` to add the executable to your PATH environment variable. This will allow you to simply type ``node`` to use Node and ``npm`` to use NPM.

        export PATH=${PATH}:~/.config/nodejs/bin/

9. (Optional) Clean up the setup files.

        cd ..
        rm -r node-v0.10.32 node-v0.10.32.tar.gz
        
Node.js should now be installed in ``~/.config/nodejs/``. The next part shall detail on how to use Node.js.

#Use

To run a file with Node.js, simply do the following:

        node <name of file to run>
        
It is recommended to run it in a screen session so that you can close the SSH connection without Node.js terminating.

##Simple HTTP Server Test

To verify that Node.js is working, the following is an easy and simple test that will run a HTTP server on a specified port. 

A random port number between 10000 and 65535 is needed and will be used to access the HTTP server that we create. The port number `{{PORT}}` has automatically been generated and will be used throughout this article, but can be changed if needed.

1. Create the file for this test

        touch test.js
        
2. Copy the contents of the box below into the test.js file

####test.js
    var http = require("http");
    var server = http.createServer(function(request, response) {
        response.write("Hello World!");
        response.end();
    });

    server.listen({{PORT}});
    console.log("Server is listening");
    
3. Start the HTTP server with the following command

        node test.js
        
If you navigate your browser to `http://{{SERVER}}.whatbox.ca:{{PORT}}/`, you should see "Hello World!".



