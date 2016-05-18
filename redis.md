# Introduction

Redis is an open source, networked, in memory key-value cache and store. It is designed to be lightweight and lightning quick. It can be used as a data structure store for an application or a cache. More information about Redis and its commands can be found at [Redis.io](http://redis.io/)

This guide hopes to cover the installation of the Redis Server and Client on your slot.

# Installation

1. Connect to your slot through [SSH](/wiki/SSH)

2. Create the installation directory for Redis

        mkdir ~/.config/redis

3. Download the Redis source

        wget http://download.redis.io/redis-stable.tar.gz

4. Extract the source and enter the directory

        tar -zxf redis-stable.tar.gz; cd redis-stable

5. Compile the source

        make

6. Run the recommend test on the build

        make test

7. If the build passes, install it in the location we made earlier

        make PREFIX=~/.config/redis/ install

8. Add the following line to ``~/.bashrc`` to add the executable to your PATH environment variable. This will allow you to simply type ``redis-server`` to use the server and ``redis-cli`` to use the client.

        export PATH=${PATH}:~/.config/redis/bin/

9. Reload your ``~/.bashrc`` to be able to use the newly added commands.

        source ~/.bashrc

10. (Optional) Clean up the setup files

        cd ..
        rm -rf redis-stable redis-stable.tar.gz 

Redis server and client should now be installed in ``~/.config/redis/``. The next part shall detail how to configure it.

# Configuration

This section will cover the configuration of the Redis server.

A random port number between 10000 and 65535 is needed and will be used by the Redis server to bind to. The port number `{{PORT}}` has automatically been generated and will be used throughout this article, but can be changed if needed.

1. Change directory to your Redis installation directory

        cd ~/.config/redis/

2. Download the default configuration file

        wget http://download.redis.io/redis-stable/redis.conf

3. Change the default port number in `redis.conf` to `{{PORT}}`

        port 6379

    to

        port {{PORT}}

4. (Optional) Uncomment the default bind address in `redis.conf` so that the Redis server will only bind to 127.0.0.1

        # bind 127.0.0.1

    to

        bind 127.0.0.1

5. (Optional) Set a password in `redis.conf` so that the Redis server requires a password before use

        # requirepass foobared

    to

        requirepass yourpassword

    Warning: since Redis is pretty fast an outside user can try up to 150k passwords per second against a good box. This means that you should use a very strong password otherwise it will be very easy to break.

The Redis server should now be configured. The next section will cover how to run the server and send commands to it.

# Use

This section will cover running the Redis server and sending commands to it with the Redis client.

1. Create a new screen session for our Redis server

        screen -S redis

2. Start the server, using the configuration file we created and modified

        redis-server ~/.config/redis/redis.conf

3. With the server running, detach from the screen session by pressing the following keys

        Ctrl + A , d

    More information about Screen can be found [here](/wiki/screen)

4. Connect to the Redis server with the Redis client. Note we have specified the port we set in the configuration file.

        redis-cli -p {{PORT}}

We should now be connected to the Redis server.

You should see the following prompt on your screen: `127.0.0.1:{{PORT}}>`. This shows the IP address and port of the Redis server we have currently connected to.

If you set the `requirepass` setting in the configuration file, type in the following to authenticate and allow you to interact with the Redis server: 

    127.0.0.1:{{PORT}}> AUTH yourpassword

If this was successful, the Redis server should return `OK` to you. If the password was incorrect, `(error) ERR invalid password` will be returned.

Now that we have connected and authenticated, we can now start issuing commands.

The following is an example for setting a key and then returning it.

    127.0.0.1:{{PORT}}> SET foo "bar"
    OK

This will set the value of `foo` to `bar`. We can get this value back by issuing the command:

    127.0.0.1:{{PORT}}> GET foo
    "bar"

And it should return `"bar"` back to us.

# Conclusion

This concludes the guide on how to install, configure and use the Redis server and client on your slot.

All of the commands and their uses can be found [here](http://redis.io/commands)


