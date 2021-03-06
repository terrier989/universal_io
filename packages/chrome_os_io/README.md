[![Pub Package](https://img.shields.io/pub/v/chrome_os_io.svg)](https://pub.dartlang.org/packages/chrome_os_io)
[![Github Actions CI](https://github.com/dart-io-packages/universal_io/workflows/Dart%20CI/badge.svg)](https://github.com/dart-io-packages/universal_io/actions?query=workflow%3A%22Dart+CI%22)

# Introduction
This package enables use of 'dart:io' networking APIs in [Chrome OS Apps](https://developer.chrome.com/apps).

Supported 'dart:io' APIs include:
  * _RawDatagramSocket_ (using [chrome.sockets.udp](https://developer.chrome.com/apps/sockets_udp))
  * _Socket_ and _RawSocket_ (using [chrome.sockets.tcp](https://developer.chrome.com/apps/sockets_tcp))
  * _ServerSocket_ and _RawServerSocket_ (using [chrome.sockets.tcpServer](https://developer.chrome.com/apps/sockets_tcpserver))

The package is implemented as a driver for [package:universal_io](https://pub.dev/packages/universal_io).
Licensed under the [Apache License 2.0](LICENSE). A few files in the package were obtained from
[package:chrome](https://pub.dev/packages/chrome) under the BSD 2-Clause License.

## Contributing
Unfortunately writing automatic tests for Chrome OS Apps is painful. At the moment, the project uses
the following manual workflow:
  1. Compile the example app.
  2. Open Chrome OS page "[chrome://extensions](chrome://extensions)".
  3. Click "Load unpacked extension"
  4. Use buttons in the web app for running tests.
  5. Look at the console (to be sure nothing is wrong).

## Related packages
  * [chrome](https://pub.dev/packages/chrome)
    * For Chrome extensions.
  * [webext](https://pub.dev/packages/webext)
    * For Google Chrome, Mozilla Firefox, and Microsoft Edge extensions.
  * [webextdev](https://pub.dev/packages/webextdev)
    * A tool for browser extension developers.

# Getting started
In _pubspec.yaml_:
```yaml
dependencies:
  chrome_os_io: ^0.1.0
```

In _main.dart_:
```dart
import 'package:chrome_os_io/chrome_os_io.dart';
import 'package:universal_io/io.dart';

void main() async {
  chromeIODriver.enable();

  // 'dart:io' works now!
  final socket = await Socket.connect("localhost", 8080);
}
```