# FeathersSwiftSocketIO

[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](#carthage) [![CocoaPods compatible](https://img.shields.io/cocoapods/v/FeathersSwiftSocketIO.svg)](#cocoapods) [![GitHub release](https://img.shields.io/github/release/feathersjs/feathers-swift-socketio.svg)](https://github.com/feathersjs/feathers-swift-socketio/releases) ![Swift 3.0.x](https://img.shields.io/badge/Swift-3.0.x-orange.svg) ![platforms](https://img.shields.io/badge/platform-iOS%20%7C%20macOS%20%7C%20tvOS-lightgrey.svg) [![Build Status](https://travis-ci.org/feathersjs/feathers-swift-socketio.svg?branch=master)](https://travis-ci.org/feathersjs/feathers-swift-socketio)

## What is FeathersSwiftSocketIO?

FeathersSwiftRest is a SocketIO provider for [FeathersSwift](https://github.com/feathersjs/feathers-swift).

## Installation

### Cocoapods
```
pod `FeathersSwiftSocketIO`
```
### Carthage

Add the following line to your Cartfile:

```
github "feathersjs/feathers-swift-socketio"
```

## Usage

To use FeathersSwiftSocket, create an instance of `SocketProvider` and initialize your FeathersSwift application:

### Quickstart

```swift
let feathersRestApp = Feathers(provider: SocketProvider(SocketIOClient(socketURL: URL(string: "https://myawesomefeathersapi.com")!, config: []), timeout: 5))
```

Configuration options can be found on [SocketIO's github](https://github.com/socketio/socket.io-client-swift).

### To listen for SocketIO events:

Initialize SocketIOClient seperately so that you have access to that class.

```swift
let socket: SocketIOClient = SocketIOClient(socketURL: URL.init(string: "https://myawesomefeathersapi.com")!, config: [.reconnects(true), .forceWebsockets(true), .compress, .log(true)])
let feathersRestApp = Feathers(provider: SocketProvider(client: socket, timeout: 10))

// Example of listening to socket disconnect event
socket.on(clientEvent: .disconnect) { (dataArray, socketAck) in
    print("Socket IO Testing .disconnect", dataArray)
    print("Socket IO Testing .disconnect", socketAck)
}
```



That's it! Your feathers application will now support a real-time socketio api.

**NOTE:** This framework does not support watchOS due to limitations with the internal SocketIO library.
