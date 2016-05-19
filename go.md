# Introduction

Go or Golang is an open source programming language created at Google. It is a compiled, statically typed language
in the style of Algol and C, with garbage collection, limited structural typing, memory safety features and CSP-style
concurrent programming features

This guide will cover how to install and configure Go, as well as how to test it with a small and simple "Hello Word"
program.

# Installation

1. Connect to your slot through [SSH](/wiki/SSH)

2. Download the latest archive

        wget https://storage.googleapis.com/golang/go1.6.2.linux-amd64.tar.gz

At the time of writing, the latest version is 1.6.2. Later versions may have been released since then. Visit
[golang.org/dl/](https://golang.org/dl/) to get the latest version. Ensure to download the Linux Intel 64 bit version.

3. Extract the archive

        tar -zxf go1.6.2.linux-amd64.tar.gz

4. Move the archive to your `~/.config/` directory

        mv go ~/.config/

5. Make your Go workspace directory

        mkdir ~/.goworkspace

6. Add the following line to `~/.bashrc`. This will allow you to simply type `go` to use Go, and set Go's workspace and
root for downloaded packages.

        export PATH=${PATH}:~/.config/go/bin/
        export GOROOT=~/.config/go/
        export GOPATH=$HOME/.goworkspace

7. Reload your `~/.bashrc` to be able to use the newly added commands.

        source ~/.bashrc

8. (Optional) Clean up the setup files.

        rm go1.6.2.linux-amd64.tar.gz

Go should now be installed in ``~/.config/go/``. The next part shall detail on how to use Go.

# Use

To run a file with Go, simply do the following:

    go run <name of file to run>

Alternatively you can 'compile' the Go program with ``go build <name of file to build>`` which will create a binary of
the file.

## Simple Hello World Test

To verify that Go is working, the following is an easy and simple test that will print `Hello world!` to the terminal.

1. Create the file for this test

        touch helloworld.go

2. Copy the contents of the box below into the helloworld.go file

#### helloworld.go
    package main

    import "fmt"

    func main() {
        fmt.Println("Hello world!")
    }

3. Start the HTTP server with the following command

        go run helloworld.go

If everything is working, you should see `Hello world!` in the terminal! You can also build the program with
`go build helloworld.go`, which means that you won't have to wait for Go to recompile the program everytime you want to
run it.

# Further Learning

Go documentation can be found on their official website at [golang.org/doc/](https://golang.org/doc/).