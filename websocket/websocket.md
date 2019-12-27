# Websocket

## What is it

- An API
- A web protocol, like HTTP, uses TCP
- full duplex communication

## Why is this so important

- Currently, the internet is ran on HTTP which means that only the client can send messages to the web server. This makes things slow.
- HTTP is stateless, so all information must be sent with each request
- While for things like loading pages, this is fine, faster stuff (like a web chat), this delay and load on the server is too much.

## How does it work

- First sets up an HTTP handshake but with a ws/wss header
- If it's successful, the server sends back a 101 status, which means that the protocol is going to be switched.
- The connection is now upgraded, but packets are still sent with TCP.
- Using TCP is why we get full-duplex communication, because packets can be sent both ways at the same time.
- This also allows multiple connections (clients, or multiple connections per client)
- Connection is closed like a HTTP close

## SSE

- Server-Sent Events API
- Uses JS eventsource interface
- This lets servers push messages to the client
- This is useful for "feeds" like twitter
