# Feature comparison of Smalltalk Web frameworks

## Abstract

A collection of frameworks where you can develop in Smalltalk (ST) and run your code in JavaScript (JS),
in the front-end (browsers, Electron, NodeGui) and the back-end (Node.js, Deno, Bun).

The following frameworks are compared in the tables below (alphabetically):\
CodeParadise (CP), PharoJS including WebST (PJS), SmallJS (SJS)

TODO: Complete PJS parts.\
TODO: More features of PJS?\
TODO: Detail pages for subjects like debugging, async.

## Feature tables

### Architecture

| Feature | CP | PJS | SJS | Remarks |
| :--- | :---: | :---: | :---: | :--- |
| JS Runtime | ST bytecode | JS code | JS code |  |
| Modular image | + |  | + | Ability to deploy specific modules instead of 'everything' |
| Support Worker Threads | + |   |   |   |
| Standalone deployment | +(1) | + | + | |
| Live code updates | +(2) |   |   | Ability to update a running application |
| JS low-level performance | - | +? | - |  |

Remarks:

1) CP can run applications standalone. In MVP-mode (when an MVP-based webapp is created) however, a Pharo server image is required as the application server.
2) CP when not running in standalone mode, will update applications immediately (on every method 'save'), without requiring any reload.

### Smalltalk support

| Feature | CP | PJS | SJS | Remarks |
| :--- | :---: | :---: | :---: | :--- |
| ST number hierarchy | +(1) |  | + | Including: LargeInteger, Float, Fraction |
| JS or ST library standard | ST |  | JS |  Uses JS or ST 'standard' classes and method names  |
| BlockClosure | + |   |   | Full Block closure including non-local returns |
| Context | + |   |   | Support for `thisContext` and other execution Context instances |
| Process | + |  |   | Execute code in own Process |
| Reflection | + |   |   | Full Object inspection/modification |
| DNU | + |   |   | Support for 'Does Not Understand' handling |
| Exception handling | + |   |   | Handle both ST as well as JS exceptions |
| Promises / async & await | +(2) |  | + |  |
| GUI model | MVP(3) |  | MVC |   |
| HTML component framework | Shoelace, Ionic |  | plain HTML |  |
| HTML generate or DOM link | both | generate | link |   |

Remarks:

1) CP does currently not support Fraction or ScaledDecimal, because they don't fit the JavaScript number types and are therefore less useful.
2) CP hides most JavaScript behavior (explicitly), so `async` and `await` keywords are never shown. Asynchronous behavior is 'visible' through Promises which are supported. On a Promise an actual 'await' can be performed which will suspend the current (Smalltalk) Process (something not possible in native JavaScript) and continu when the Promise has settled (either resolved or rejected).
3) CP supports multiple GUI models including an elaborate MVP-model in which code in the browser is only a (Passive) View (see Fowler).

### Front-end environments / frameworks

| Feature | CP | PJS | SJS | Remarks |
| :--- | :---: | :---: | :---: | :--- |
| Browser support:  | C,F,S |  | C,F | Chromium, Firefox, Safari |
| Desktop support | ?(1) |  | E,N | Electron, NodeGui |

Remarks:

1) CP is not tested within Election nor NodeGui environment. There is no explicit support for the NodeGui framework implemented.

### Back-end environments / frameworks

| Feature | CP | PJS | SJS | Remarks |
| :--- | :---: | :---: | :---: | :--- |
| Node.js | + |  | + |  |
| Deno | ? |  | ? | ? = untested |
| Bun | + |  | ? | ? = untested |
| HTTP server | Zinc or "node:https" | Zinc | Http-sever |  |
| App server | CP(1) | Seaside? | ExpressJS |  |
| Database support | S(2) |  | S,P,M | SQLite, Postgres, MySQL / MariaDB  |
| AI support | - |  |  | Soon: OpenAI, DeepSeek |

Remarks:

1) CP has its own Application Server when running in MVP-mode. CP can also be run on JavaScript-only mode with a REST API Server (also part of CP).
2) CP supports a wide range of databases (all Pharo supported databases, from Gemstone to Sqlite) when run in MVP-mode. When run in a Node.js (like) environment, only support for Sqlite is present at the moment.

### Development

| Feature | CP | PJS | SJS | Remarks |
| :--- | :---: | :---: | :---: | :--- |
| IDE | Pharo(1) | Pharo | VSCode |  |
| Live image | + | + | - |  |
| Image or File based | Image | Image | File |  |
| Separate HTML / CSS files (tooling) | - |  | + |  |
| Playground | +(2) |  | + |  |
| Git tools | Metacello | Metacello | all file based |  |
| JS / TS source-level integration | -(3) |  | + |  |

Remarks:

1) CP has a few development tools running in the browser as well (when creating webapps).
2) CP allows 'remote' code execution from the Pharo IDE to the tiny image running in the browser (or within a Node.js environment).
3) CP explicitly tries to hide any JavaScript (source) code. No source-level integration will (ever) be shown. The integration with JavaScript is on the runtime/execution level (calling existing JavaScript code). The user/developer can however create a &lt;script&gt; tag to create some function which can then be called from a Smalltalk object.

### Debugging

| Feature | CP | PJS | SJS | Remarks |
| :--- | :---: | :---: | :---: | :--- |
| ST source debugging | +(2) |  | + | SJS through source map |
| ST step debugging | -(2) |  | + |  SJS shows ST wrappers in JS (1) |
| JS source debugging | -(3) |  | + |  |
| JS runtime debugging | -(3) |  | + |  |
| async debugging | -(3) |  | + |  |

Remarks:

1) Would need VSCode Language server prevent, but that's a lot of effort
and would hide the JS running underneath.
2) CP currently has full insight into the (Smalltalk) call stack including context/object inspection and showing related source code. Objects can however not be modified yet and code can not be stepped at the moment.
3) CP does not support JavaScript source code in any way (see (2) at paragraph Development above). Debugging can't be done on the JavaScript source-level (and should not be done on JavaScript source-level, since in CP you don't write any JavaScript code). Exception handling on the JavaScript runtime/execution level is supported, which allows detection and visualisation of errors/issues. This can be useful in combination with the browser's typical dev-tools.
