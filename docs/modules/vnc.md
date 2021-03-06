# VNC

Grab VNC information and screenshots.

## VNC Request Example

```
curl -v -L https://api.binaryedge.io/v1/tasks -d '{"type":"scan", "options":[{"targets":["X.X.X.X"], "ports":[{"port":5900, "protocol":"tcp", "modules":["vnc"]}]}]}' -H "X-Token:<Token>"
```

## Schema

### VNC Event Schema

```json
{
  ...
  "result": {
    "data": {
      "title": "string",
      "width": "string",
      "height": "string",
      "version": "string",
      "link": "string",
      "auth_enabled": "boolean",
      "msg": "string"
    }
  }
}
```

### Contents of the fields:

* title - Title returned by the VNC server
* width - Width of the screen
* height - Height of the screen
* version - Version of the VNC Protocol
* link - URL link to the screenshot
* msg - Warning sent by the server, for example, "Too many security failures".

## VNC Event Example

```json
{
  "origin": {
    "type": "vnc",
    "job_id": "client-816f1185-4bc1-4b5f-9a7d-61a2df315a6b",
    "client_id": "client",
    "country": "uk",
    "module": "grabber",
    "ts": 1453385574412
  },
  "target": {
    "ip": "X.X.X.X",
    "port": 5900,
    "protocol": "tcp"
  },
  "result": {
    "data": {
      "title": "TC13:0.0",
      "width": "1280",
      "height": "1024",
      "version": "RFB 003.007",
      "link": "https://url/to/image.jpg"
      "auth_enabled": "false"
    }
  }
}
```
