bash\_udp
========

UDP server for bash (using netcat).

This is obviously a terrible idea. It works by calling out to netcat **for every packet**.

# Usage

See example.sh for usage.

# Bugs

Seriously?

- A new netcat process has to be spawned for every packet. This causes a crazy amount of CPU to be used, but hey, it's bash. Also, this will lead to crazy packet loss.
	- It's hard to use netcat to receive more than one packet. This seems to lock you into one connection (localport, remoteport, remotehost tuple) per process. However, this might be better if you don't necessarily expect connections from multiple hosts/ports. You can mess with the nc line if you want to try this out (something like -w10 instead of -w0).
- The library doesn't report who sent the packet. This can probably be fixed by listening to netcat's stderr, but is left as an exercise to the reader.
- The packet is presented as a single line. Any newlines are turned into whitespace, and other terrible things are probably done to it as well.
