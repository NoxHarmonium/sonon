# Sonon

An attempt at creating a client for a Sonoff TH10 device 
that will act as a bridge between other services
with the eventual goal of sending temprature stats
to [Carbon](https://github.com/graphite-project/carbon) 
so they can be graphed with Graphite.

It could also be used to create an app that
can be accessed from multiple devices at once.
The EWeLink app provided to connect to the 
Sonoff devices will only allow 
one person to connect at a time.

## Current Status

So far I have captures requests using the
[Charles](https://www.charlesproxy.com/)
web proxy and have built a swagger model
for the following endpoints:

- https://api.coolkit.cc:8080/api
- https://us-api.coolkit.cc:8080/api

The first one is used globally for initial
authentication but then a region is returned.
The second endpoint is the us region endpoint
that was used as my account is a US account.

The swagger files do not capture all the
requests and responses that are sent
while using the app but they capture
the most important interactions 
which will be enough to get a basic client going.

All control messages to the device itself
and feedback about its state such as
temprature are sent via a websocket
API at another endpoint
(wss://us-long.coolkit.cc:8080/api/ws).
I have started to capture the interactions
via this API in a [traces file](traces/ws-trace.md).

## Next Steps

- Generate a web client with the swagger files (probably Node.js).
- Manually implement the web socket interactions.
- Lots more!
