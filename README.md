bash\_udp
========

UDP server for bash (using netcat).

This is obviously a terrible idea. It works by calling out to netcat **for every packet**.

# Usage

See example.sh for usage.

# Bugs

Seriously?

- A new netcat process has to be spawned for every packet. This causes a crazy amount of CPU to be used, but hey, it's bash.
- The library doesn't report who sent the packet. This can probably be fixed by listening to netcat's stderr, but is left as an exercise to the reader.
- The packet is presented as a single line. Any newlines are turned into whitespace, and other terrible things are probably done to it as well.
