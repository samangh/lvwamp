# wamplv

A LabVIEW-based client for the [Web Application Messaging Protocol
(WAMP)](https://wamp-proto.org/). _wamplv_ supports the WAMP basic
profiles for client roles.

  * Platform: Windows, Linux, macOS and Real Time targets
  * Roles: caller, callee, subscriber and publisher
  * Transport: WebSocket, RawSocket TCP (including TLS/SSL support for
    both)
  * Message Serialisation: JSON

This library will only work on LabVIEW 2020 or later.

The library is designed to give you complete flexibility in how you use
WAMP:

 * All actions can be done either synchronously or
   asynchronously. If an asynchronous VI is used, the result is
   available via a notifier;
 * Once subscribed to a topic, you can choose to receive the topic
   events via either LabVIEW user events or a queue;
 * Once you've registered an endpoint, you can receive the invocations
   either vi user event or via a queue.

## Installation

You can install it using the VI package manager.

_wamplv_ is available on the VIPM Community repository. Alternatively,
the VI package is also available to download
[here](https://github.com/samangh/wamplv/releases).

## Quick start

The VIs in the `Example` folder will show you how to get started.

![Example](images/example.png)

Important points:

* The router address must be a fully formed URI, including the port. Some
   examples: 
    * `tcp://localhost:8080/`
    * `tcps://loclhost:8080/`
    * `ws://localhost:80/`
    * `ws://localhost:80/ws`
    * `wss://localhost:80/`
 * Remember to **always** call `Disconnect.vi` at the end of your
   program. This will disconnect from the router and stop the
   communication daemon. Simply stopping the VI is not enough as the
   _wamplv_ communication daemon runs asynchronously in the background.
  * If you have finished using the WAMP client after disconnecting
    (i.e. will not reconnect), call `Cleanup.vi` to cleanup any internal
    DVRs and unregister the user events that _wamplv_creates.

See the [user guide](guide.md) for more details.

## License

Licensed under LGPG v2.1 with exceptions. See [LICENSE](LICENSE).
