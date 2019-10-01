# Basic P2P messaging app

_Spec v1 (2019-06-28)_

The task is to create a very basic p2p (peer-to-peer) &ndash; and as simple as possible &ndash; messaging application. P2P in this context means that no 3rd party server can be used to connect the messaging participants and all communication (on application layer) must happen only between the participants. Messaging happens only between two parties so no chat rooms etc. are required. All required storage is in memory &ndash; no history between application runs is required.

UI (user interface) is not important. It can be a CLI (command-line-interface) or a web app or whatever the implementer seems necessary. **UI design and style will not be evaluated.** The only goal of the UI is to prompt the user for a username and the IP and port of the other participant and make it possible to send and read messages.

The goal is _not_ to create a full-fledged messaging application but to create an application just capable of exchanging messages between two parties.

## Requirements

- As basic and simple as possible
- Use any programming language you prefer
- Send messages containing:
  - `timestamp`
  - `username`
  - `message`
- Receive messages
- List received and sent messages in format:
  - `[timestamp] username: message`
  - `timestamp` in some human readable short format
- Only p2p communication (no 3rd party server)
- No encryption
- Interoperable with the other implementation
  - The two implementations need to be able to communicate (send and receive messages) with one another
  - This refers to Muhammads implementation
- Able to run multiple instances of the application on the same host
- Evaluator must be able to build and run the application from source code
  - Make it as simple as possible to build and run the application
  - Docker can be used
