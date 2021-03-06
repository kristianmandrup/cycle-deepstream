cycle-deepstream
=====================

[![Join the chat at https://gitter.im/EnigmaCurry/cycle-deepstream](https://badges.gitter.im/EnigmaCurry/cycle-deepstream.svg)](https://gitter.im/EnigmaCurry/cycle-deepstream?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

A [Cycle.js](https://cycle.js.org/) driver for [deepstream.io](https://deepstream.io)

Status: *experimental* - not released on npm yet.

![giphy](https://cloud.githubusercontent.com/assets/43061/23532850/f8351d38-ff7b-11e6-9645-905309d7ee05.gif)

Run Demo
----------
Get the code:

    git clone https://github.com/EnigmaCurry/cycle-deepstream.git
    cd cycle-deepstream
    
Run the comprehensive demo:

    npm run comprehensive

Or run the simple example:

    npm run simple

Features
----------

Deepstream API Implementation:
  - Client
    - [x] login
    - [x] logout
    - events:
      - [x] onConnectionChange
      - [x] client.error
      - [x] login.success
      - [x] login.failure
      - [x] logout
  - Records:
    - [x] record.subscribe
       - Note: Only one subscription is supported per record, and no
         paths or callbacks are supported. Because the record
         subscription is broadcast to all driver listeners, only one
         subscription is ever needed. Subsequent record.subscribe
         requests for the same id are ignored unless you call
         record.discard first.
       - once subscribed, will emit events:
         - [x] record.change
         - [x] record.discard
         - [x] record.delete
         - [x] record.error
    - [x] record.set
    - [x] record.get
    - [x] record.snapshot
    - [x] record.discard
    - [x] record.delete
    - [x] record.listen
    - [ ] record.unsubscribe 
      - Not implemented. There is only ever one subscription per
        record, so use record.discard instead.
    
  - Lists:
    - [x] list.subscribe
       - Note: Only one subscription is supported per list, and no
         paths or callbacks are supported. Because the list
         subscription is broadcast to all driver listeners, only one
         subscription is ever needed. Subsequent list.subscribe
         requests for the same id are ignored unless you call
         list.discard first.
      - once subscribed, will emit events:
         - [x] list.change
         - [x] list.entry-existing
           - This emits individual events for each existing entry, like list.entry-added.
           - Note, this is a driver level event, not a part of the Deepstream API.
         - [x] list.discard
         - [x] list.delete
         - [x] list.error
         - [x] list.entry-added
         - [x] list.entry-moved
         - [x] list.entry-removed
    - [x] list.getEntries
    - [x] list.setEntries
    - [x] list.addEntry
    - [x] list.removeEntry
    - [x] list.discard
    - [x] list.delete
    - [ ] list.unsubscribe
      - Not implemented. There is only ever one subscription per
        list, so use list.discard instead.
    
    
  - Events:
    - [ ] event.subscribe
    - [ ] event.unsubscribe
    - [ ] event.emit
    - [ ] event.listen
    
  - Presence:
    - [ ] presence.subscribe
    - [ ] presence.unsubscribe
    - [ ] presence.getAll
    
  - RPC:
    - [ ] rpc.make
    - [ ] rpc.provide - I think this makes no sense to implement in cycle?

TODO
-----

 [ ] - Testing... lol.
