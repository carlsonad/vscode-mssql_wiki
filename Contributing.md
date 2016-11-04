# Contributor Guide
The instructions below will help you set up your development environment to contribute to this repository.
Make sure you've already cloned the repo.  :smile:

## Ways to Contribute
Interested in contributing to the mssql project? There are plenty of ways to contribute, all of which help make the project better.
* Submit a [bug report](https://github.com/Microsoft/vscode-mssql/issues/new) or [feature suggestion](https://github.com/Microsoft/vscode-mssql/issues/new) through the Issue Tracker
* Review the [source code changes](https://github.com/Microsoft/vscode-mssql/pulls)
* Submit a code fix for a bug (see `Submitting Pull Requests` below)
* Participate in [discussions](https://github.com/Microsoft/vscode-mssql/issues) or [gitter](https://gitter.im/Microsoft/mssql)

## Set up Node, npm and gulp

### Node and npm
**Windows and Mac OSX**: Download and install node from [nodejs.org](http://nodejs.org/)

**Linux**: Install [using package manager](https://nodejs.org/en/download/package-manager/)

From a terminal ensure at least node 5.4.1 and npm 3:
```bash
$ node -v && npm -v
v5.9.0
3.8.2
```
**Note**: To get npm version 3.8.2, you may need to update npm after installing node.  To do that:
```bash
[sudo] npm install npm -g
```

### Gulp
Install gulp
```bash
[sudo] npm install gulp -g
```
From the root of the repo, install all of the build dependencies:
```bash
[sudo] npm install --greedy
```

### Install the Visual Studio Code Extension Manager (VSCE)
Before packaging via gulp, ensure that you have the "vsce" tool installed globally.  Otherwise, the package step will fail.

From the root of the repo, run:
```bash
[sudo] npm install vsce -g
```

## Build
To build the extension, run the following from the root of the repo:

```bash
gulp build
```
This command will create the out\src and out\test folders at the root of the repository. 

## Tests
Tests should be run with changes.  Before you run tests, make sure you have built the extension.  Run the following from the root of the repo:

```bash
gulp test
```
To run the tests within Visual Studio Code, change the debug profile to "Launch Tests" and press `F5`.

## Package
The package command will package the extension into a Visual Studio extension installer (.vsix file).
It will also transpile the TypeScript into the out\src and out\test folders.

From the root of the repo:
```bash
gulp package
```
The VSIX package will be created in the root of the repository.

## Submitting Pull Requests
We welcome pull requests!  Fork this repo and send us your contributions.  Go [here](https://help.github.com/articles/using-pull-requests/) to get familiar with GitHub pull requests.

Before submitting your request, ensure that both `gulp build` and `gulp test` succeed.
