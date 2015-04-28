# Introduction

XMLRPC is used by rTorrent as a means for sending and receiving information from the server. Queries can be made to retrieve information about current torrents as well as executing commands, for example pausing a torrent.

This guide hopes to cover using Python to interact with the rTorrent server. This allows us to write scripts that can automate the use of our rTorrent server. 

## Use Cases

Some use cases of using Python to interact with your rTorrent server through XMLRPC might be:

+ Script to automatically remove a torrent when it has seeded a certain amount
+ Web interface using [Flask](http://flask.pocoo.org/) or [Bottle](http://bottlepy.org/docs/dev/index.html) to display torrent information
+ Script with a cron job to periodically send information about currently running torrents to an email address
+ + Many more!

# XMLRPC Login Details

The login details for the XMLRPC interface on your rTorrent server are as follows:

<table class="mini">
<tr><td>Protocol: </td><td><code>HTTP</code></td></tr>
<tr><td>Host: </td><td><code>{{SERVER}}.whatbox.ca</code></td></tr>
<tr><td>Port: </td><td><code>80</code></td></tr>
<tr><td>Mountpoint: </td><td><code>/xmlrpc</code></td></tr>
<tr><td>Username: </td><td><code>{{USER}}</code></td></tr>
<tr><td>Password: </td><td><code>(Your password)</code></td></tr>
</table> 

We will use this information to connect to your server.

# Python Script

This section contains an example Python script and will have comments within it explaining what it does.

The library [xmlrpclib](https://docs.python.org/2/library/xmlrpclib.html) is required for this script to function. It should already by installed on your slot, so there is no need to install it.

#### script.py
    # Import the XMLRPC library
    import xmlrpclib

    # Create an object to represent our server. Use the login information in the XMLRPC Login Details section here.
    server_url = "http://{{USER}}:(Your password)@{{SERVER}}.whatbox.ca:80/xmlrpc";
    server = xmlrpclib.Server(server_url);

    # Get torrents in the main view
    mainview = server.download_list("", "main")

    # For each torrent in the main view
    for torrent in mainview:

        # Print the name of torrent
        print server.d.get_name(torrent)
        # Print the directory of torrent
        print server.d.get_directory(torrent)

This script essentially connects to the XMLRPC interface of the rTorrent server, retrieves a list of the torrents in the main view, and then for each of those torrents, gets the name of the torrent and the directory of the torrent.

Due to the easy use of Python, creating scripts to interact with the XMLRPC interface of an XMLRPC server is painless.

