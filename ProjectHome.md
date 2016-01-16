Moquette aims to be a MQTT compliant broker. The broker supports QoS 0, QoS 1 and QoS 2.

Its designed to be evented, uses Netty for the protocol encoding and decoding part, the protocol logic is essentially a single threaded and it's isolated from front connectors part by LMAX disruptor's ring buffer.

**Project moved to GitHub** (https://github.com/andsel/moquette)