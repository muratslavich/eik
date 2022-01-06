# HTTP

Http is a protocol for transferring resources such as html or json.

{% embed url="https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview" %}

Requests are initiated by the recipient.

Application layer protocol that sents over TCP or TLS/TCP.

#### Http is extensible

Http [headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers) make it by agreement between a client and a server about headers semantic.

#### Http is stateless, but not sessionless

No state between two requests. To interact between two requests coherently exists HTTP cookies. Cookies allow share context.

#### Http connection

Connection is controlled on the transport layer by TCP, therefore not managed by HTTP.&#x20;

* HTTP/1.0 - open separate TCP connection for each request
* HTTP/1.1 - pipelining, TCP connection partially controlled by Connection header
* HTTP/2 - multiplexing messages, keep connection warm

```
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
```

```
HTTP/1.1 200 OK
Date: Sat, 09 Oct 2010 14:28:02 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
ETag: "51142bc1-7449-479b075b2891b"
Accept-Ranges: bytes
Content-Length: 29769
Content-Type: text/html

<!DOCTYPE html... (here come the 29769 bytes of the requested web page)
```

### Methods

[`GET`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/GET) `` The `GET` method requests a representation of the specified resource. Requests using `GET` should only retrieve data.

[`HEAD`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/HEAD) `` The `HEAD` method asks for a response identical to a `GET` request, but without the response body.

[`POST`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST) `` The `POST` method submits an entity to the specified resource, often causing a change in state or side effects on the server.

[`PUT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PUT) `` The `PUT` method replaces all current representations of the target resource with the request payload.

[`DELETE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/DELETE) `` The `DELETE` method deletes the specified resource.

[`CONNECT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/CONNECT) `` The `CONNECT` method establishes a tunnel to the server identified by the target resource.

[`OPTIONS`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/OPTIONS) `` The `OPTIONS` method describes the communication options for the target resource.

[`TRACE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/TRACE) `` The `TRACE` method performs a message loop-back test along the path to the target resource.

[`PATCH`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PATCH) `` The `PATCH` method applies partial modifications to a resource.

### Responses

1. [Informational responses](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#information\_responses) (`100`–`199`)
2. [Successful responses](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#successful\_responses) (`200`–`299`)
3. [Redirection messages](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#redirection\_messages) (`300`–`399`)
4. [Client error responses](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client\_error\_responses) (`400`–`499`)
5. [Server error responses](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#server\_error\_responses) (`500`–`599`)
