v0.6.4
======

* Add `Subscription.Close` method to close Subscription when it's not needed anymore. This method unsubscribes from a channel and removes Subscription from internal `Client` subscription registry – thus freeing resources. Subscription is not usable after `Close` called. This method can be helpful if you work with lots of short-living subscriptions to different channels to prevent unlimited internal Subscription registry growth.

v0.6.3
======

* Fix memory align on 32bit arch, see [#40](https://github.com/centrifugal/centrifuge-go/pull/40)

v0.6.2
======

* fix deadlock on a private channel resubscribe - see [#38](https://github.com/centrifugal/centrifuge-go/pull/38)

v0.6.1
======

* fix setting server-side unsubscribe handler, call server-side unsubscribe event on disconnect 

v0.6.0
======

* server-side subscriptions support
* get rid of Protobuf protocol struct `Publication` and `ClientInfo` aliases – use library scope structures instead
* change return values of `RPC`, `NamedRPC`, `History`, `Presence`, `PresenceStats`, `Publish` methods to be more meaningful and extensible
* much faster resubscribe to many subscriptions (previously we waited for each individual subscription response before moving further, now process is asynchronous)
* improved reconnect logic
* Client and Subscription status refactoring
* fix inconsistent join/subscribe event ordering – now both processed in order coming from server

v0.5.2
======

* `NamedRPC` method added - [#35](https://github.com/centrifugal/centrifuge-go/pull/35), thanks [@L11R](https://github.com/L11R)
