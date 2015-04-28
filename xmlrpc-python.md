#Introduction

XMLRPC is used by rTorrent as a means for sending and receiving information from the server. Queries can be made to retrieve information about current torrents as well as executing commands, for example pausing a torrent.

This guide hopes to cover using Python to interact with the rTorrent server. This allows us to write scripts that can automate the use of our rTorrent server. 

##Use Cases

Some use cases of using Python to interact with your rTorrent server through XMLRPC might be:

+ Script to automatically remove a torrent when it has seeded a certain amount
+ Web interface using [Flask](http://flask.pocoo.org/) or [Bottle](http://bottlepy.org/docs/dev/index.html) to display torrent information
+ + Many more!

#XMLRPC Login Details

The login details for the XMLRPC interface on your rTorrent are as follows:

<table class="mini">
<tr><td>Protocol: </td><td><code>HTTP</code></td></tr>
<tr><td>Host: </td><td><code>{{SERVER}}.whatbox.ca</code></td></tr>
<tr><td>Port: </td><td><code>80</code></td></tr>
<tr><td>Mountpoint: </td><td><code>/xmlrpc</code></td></tr>
<tr><td>Username: </td><td><code>{{USER}}</code></td></tr>
<tr><td>Password: </td><td><code>(Your password)</code></td></tr>
</table> 

We will use this information to connect to your server.

