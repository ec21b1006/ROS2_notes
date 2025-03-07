source: https://docs.ros.org/en/humble/Concepts/Intermediate/About-Domain-ID.html#id3

# Not so straighforward things on the source available

**Finding the Highest Domain ID**

Since **UDP ports are limited to 65535**, let's determine the **maximum possible domain ID**:

`Max Port=65535`

`Base Port+(Max Domain ID×250) ≤ 65535`

Substituting **Base Port = 7400**:

`7400 + {Max Domain ID} x 250) ≤ 65535`

`7400+(Max Domain ID×250)≤65535`

`Max Domain ID ≤ (65535−7400)/250​ = 58135/250 ​= 232.54`

Since the domain ID is an **integer**, the highest valid **Domain ID** is **232**.

## Ephemeral Port 

- An **ephemeral port** is a communications endpoint ([port](https://en.wikipedia.org/wiki/Port_%28computer_networking%29)) of a [transport layer](https://en.wikipedia.org/wiki/Transport_layer "Transport layer") protocol of the [Internet protocol suite](https://en.wikipedia.org/wiki/Internet_protocol_suite "Internet protocol suite") that is used for only a short period of time for the duration of a communication session. Such short-lived ports are allocated automatically within a predefined range of [port numbers](https://en.wikipedia.org/wiki/Port_number "Port number") by the [IP stack](https://en.wikipedia.org/wiki/IP_stack "IP stack") software of a computer operating system.
- The allocation of an ephemeral port is temporary and only valid for the duration of the communication session. After completion of the session, the port is destroyed and the port number becomes available for reuse

&nbsp;       **32768–60999** : used by many Linux kernels

&nbsp;       **1024–5000** : Default range of Microsoft Windows operating systems through Windows XP.

This means that domain **IDs 0-101 and 215-232** can be safely used without colliding with ephemeral ports. The ephemeral port range is configurable in Linux by setting custom values in `/proc/sys/net/ipv4/ip_local_port_range`. If a custom ephemeral port range is used, the above numbers may have to be adjusted accordingly.

&nbsp;