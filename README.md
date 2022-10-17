# dart-build-runner
Dart build runner --live-reload issue repro

According to [build_runner documentation](https://pub.dev/packages/build_runner):

> Some commands also have additional options:

> serve
> --hostname: The host to run the server on.
> --live-reload: Enables automatic page reloading on rebuilds.


## Steps

1. dart pub get
2. dart run build_runner serve --live-reload
3. Open http://localhost:8080/

## Issue

The application is built and served, but live-reload doesn't work, with the following error: 

```
Serving `web` on http://localhost:8080
ERROR - 2022-10-17 10:06:11.398101
Asynchronous error
NoSuchMethodError: Closure call with mismatched arguments: function 'BuildUpdatesWebSocketHandler.createHandlerByRootDir.closureForRootDir'
Receiver: Closure: (WebSocketChannel, String) => void
Tried calling: BuildUpdatesWebSocketHandler.createHandlerByRootDir.closureForRootDir(Instance of 'WebSocketChannel')
Found: BuildUpdatesWebSocketHandler.createHandlerByRootDir.closureForRootDir(WebSocketChannel, String) => void
dart:core                                                   _objectNoSuchMethod
package:shelf_web_socket/shelf_web_socket.dart 49:55        webSocketHandler.<fn>
package:shelf_web_socket/src/web_socket_handler.dart 81:20  WebSocketHandler.handle.<fn>
```