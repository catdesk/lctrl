# ltctrl

Simple command line interface to control RGB light strip, best used in conjuction with the gem serialport-server but any service that takes in messages from POST requests and passes them along to the serial port will work. Using this you can control a RGB light strip connected to another computer that is exposing an API. 

Included is arduino code to accept json structures that provide brightness of each red, blue and green between 0-255 and the speed of which to fade to that brightness.

## Installation

An install script has been included to simplyify installation but the basic instructions are below:

Install the dependencies

    bundle

To install it is best to put the lctrl executable your bin folder:

    cp lctrl /usr/local/bin
    cp lsrvr /usr/local/bin

Then you copy the config file to your home directory, update the config to suite your needs

    cp config/config.sample.yml ~/.lctrl.yml

Then start the server

    lsrvr -s desk -d

Then you can use the ltctrl command to control the lights. 

## Usage

For the command line interface:

    Usage:
    Please specify colors by name, json or rgb:
        lctrl [options]
    Options:
        --server [option]       # Specify the server from the configuration file
        --red    [option]       # Provide a number 0-255, 0 being off and 255 being the brightest
        --green  [option]       # Provide a number 0-255, 0 being off and 255 being the brightest
        --blue   [option]       # Provide a number 0-255, 0 being off and 255 being the brightest
        --color  [option]       # Select between, "red", "blue", "green" or "white"
        --json   [json]         # Supply json directly: {"red": 0, "blue": 255, "green", 0}
        --random                # Randomly select a color
        --off                   # Turns off the lights
    Example:
        lctrl --green 255 --blue 24
        lctrl -g 255 -b 24


For the server daemon:

    Usage:
    Please specify the server defined in the configuration to start:
        lsrvr [options]
    Options:
        --server [option]       # Provide a server defined in the config file
        --daemon                # Daemonize the server
    Example:
        lctrl --server wall
        lctrl -s wall

## Roadmap

If I have time in the future I would like to add more configuration options, you should be able to specify if you would like to send the message directly over serial and what port, or over websockets, or over TCP.
