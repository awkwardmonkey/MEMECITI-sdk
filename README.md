# MEMECITI SDK

The **MEMECITI SDK** is a JavaScript/TypeScript SDK for developing web-based applications for virtual worlds. MEMECITI domain servers provide the worlds (a.k.a. "domains") to visit, and the MEMECITI Memeverse Server provides global services that connect the users and domains.

This SDK provides interfaces to:
- Connect to domains.
- Use Memeverse services.

The SDK is written in TypeScript.
- [Project Configuration](CONFIGURATION.md)
- [Coding Standard](CODING_STANDARD.md)

## Prerequisites

### Node.js

https://nodejs.org/en/download/

**Node.js** version &ge; 10.13 ; LTS version &ge; 14.16 recommended  
**npm** version &ge; 6.4.1 ; LTS version &ge; 6.14 recommended

### Jest

[Jest](https://jestjs.io/) is used for unit testing. It is included as an NPM dev dependency, however, you may also install it globally if you want
to. 

## Project Setup

### Get the source

```
git clone https://github.com/awkwardmonkey/memeciti-sdk.git
```

If you're working on Memeland protocol code (that in the `\src\domain` directory) it is recommended that you clone the SDK as
a subdirectory of the main Memeland repo's source so that both sets of code are accessed when you open the main Memeland repo's
source in your IDE. For example, if your clone of the main Memeland repo's source is in `C:\Workspaces\memeciti` then clone
the SDK repo's source into `C:\Workspaces\memeciti-sdk`. Thus with the main Memeland's repo loaded in your IDE, when
you search for code then both C++ and TypeScript results are returned, helping you compare the two codebases and keep them in
sync.

Note: Unix line endings (LF, `0A` character) are used. If using Windows it is recommended that you configure Git's global setting `core.autocrlf` to be `true`. This makes the files use Windows line endings (CRLF, `0D0A` characters) on your computer but stores the files in the Git repo with Linux line endings.


### Install NPM packages

```
npm install
```
Loads all the supporting NPM packages as defined in `package.json` into the `node_modules` directory.

## Development and Testing

### Compile and minify for development
```
npm run build
```
Does a development compile and packages the SDK into the `dist` directory.

### Hot-recompile for development
```
npm run watch
```
Does a development compile and enables webpack to watch the sources and recomile when source files change.
This is often useful when testing SDK development using the `example` tool.

### Compile and minify for production
```
npm run build-prod
```
Does a clean production compile and packages a releasable version of the SDK into the `dist` directory.

### Hot-recompile for production
```
npm run watch-prod
```
Does a clean production compile and enables webpack to watch the sources and recompile when the source files change.

### Clean the build directory
```
npm run clean
```

### Lint files

All files:
```
npm run lint
```

A specific directory or file:
```
npm run lint-path <path>
```

### Run tests

Unit tests can be run without any external dependencies but integration tests require a domain server to be running on
`localhost` or other location specified in `./tests/test.config.json`. The location and other values of the config JSON can be
overridden with environment variables, using the same property names, but prefixed with "MEMELAND_".

All tests:
```
npm run test
```
Hot retest of all tests:
```
npm run test-watch
```

Specific tests (e.g., Packet.unit.test.js, all unit tests, all integration tests):
```
npm run test <partial-path>

npm run test /packet.unit
npm run test .unit.
npm run test .integration.
```

Run tests and report open handles:
```
npm run test-debug [<partial-path>]
```


### Generate docs

SDK API documentation:
```
npm run sdkdoc
```

Developer documentation (includes SDK API documentation):
```
npm run devdoc
```

### Update contributors

Update contributors list in package.json:

```
npm run update-contributors
```
