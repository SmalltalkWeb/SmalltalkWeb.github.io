# Use Cases

This describes and compares intended target use cases and user audiences
of the Smalltalk web frameworks (alphabetically): CodeParadise, PharoJS (including WebST), SmallJS

TODO: Complete PJS parts.

## CodeParadise

CodeParadise is a framework for developing web applications, Node.js applications and mobile apps in Smalltalk only. CodeParadise therefore targets Smalltalk fans and addicts alike. CodeParadise is based on the Pharo Smalltalk environment, so previous experience with this IDE is beneficial. CodeParadise integrates with a JavaScript environment on the runtime/execution level. No need to write ANY JavaScript source code, but still use all existing libraries and frameworks. Using existing code is done by creating thin wrapper classes for the JavaScript code (or using one of the existing ones, including some generic Proxy objects).
CodeParadise offers live code updates giving the joy and pleasure many developers have found in using Smalltalk's live programming experience. Full Smalltalk support is present from reflection, error handling to multi-processes and context instances. At the same time CodeParadise supports JavaScript concepts like Promises, Events and allows DOM manipulation and/or creation of WebComponents.

## PharoJS / WebST

Existing Pharo users that want to develop in the Pharo live image IDE as long as possible,\
before deploying to a browser or NodeJS.
[...]

## SmallJS

Targets existing JS / TS users that want to use a more elegant, consistent language than JS.\
Incremental use is possible, while leveraging knowledge of the DOM / Node.js frameworks,\
that are directly accessible without translation layers.\
Using the same, single language / framework for both back-end and front-end development,\
and easy modular deployment, also for complex applications.\
Productivity with full, native debugging support form all supported runtime environment.
