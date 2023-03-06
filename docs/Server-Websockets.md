---
stoplight-id: ns0yjmwuq5qge
tags: [Server]
---

# Server Websockets

## Event Schema
```json jsonSchema
{
  "type": "object",
  "title": "Event",
  "description": "An event that could be sent to the server or could be received from the server.",
  "properties": {
    "event": {
      "type": "string",
      "description": "The event type.",
      "enum": [
        # sent by client
        "auth",
        "send stats",
        "send logs",
        "set state",
        "send command",
        # sent by server
        "auth success",
        "status",
        "console output",
        "stats",
        "token expiring",
        "token expired"
      ]
    },
    "args": {
      "type": ["array", "null"],
      "nullable": true,
      "description": "The arguments for (of) that event."
    }
  }
}
```

## Event Types
### Sent by client
#### "auth"
```yaml jsonSchema
title: Arguments
type: [array, "null"]
example: ["eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiIsImp0aSI6IjXa7WhE9h1uweWea01IkaPo1"]
minItems: 1
maxItems: 1
uniqueItems: true
items:
  - type: string
    example: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiIsImp0aSI6IjXa7WhE9h1uweWea01IkaPo1
    format: password
```
#### "send stats", "send logs"
```yaml jsonSchema
title: Arguments
type: array
example: "[null]"
items:
  - type: null
    example: "null"
```
#### "set state"
```yaml jsonSchema
title: Arguments
type: array
example: "[\"start\"]"
items:
  - type: string
    enum: [start, stop, restart, kill]
```
#### "send command"
```yaml jsonSchema
title: Arguments
type: array
maxItems: 1
minItems: 1
description: The panel invokes the command (first element of "args") after receiving this event.
example: "[\"say I am the Server, muahahaha!\"]"
items:
  - type: string
    description: The command to be sent
```
### Sent by server
#### "auth success"
An event sent by the server, indicating that the authentication with the token sent by the client with the [`auth`](#"auth") event. \
**Has no arguments.**
#### "status"
An event sent by the server, indicating a status change, e.g. server is now offline etc.
```yaml jsonSchema
title: Arguments
type: array
example: "[\"offline\"]"
maxItems: 1
minItems: 1
items:
  - type: string
    description: The current status of the server.
    enum: [offline, running, starting, stopping]
```