What is it?
===========

This repository contains a framework for implementing zero-sum game
engines and some reference games implemented with it.

Samurai Framework
=================

Samurai is a generic framework for implementing search engines for
zero-sum games. It provides a variety of algorithms and tools that can
be used to develop engines for a wide range of games, including:

* UCI protocol support for any game.
* Base open-book implementation.
* Search algorithms: UCT, Negamax, Monte-Carlo, etc.
* Generic EGTB implementation.
* Generic transposition table implementation.
* Generic automatic opening-book generator.
* Position and move representation utilities.
* Utilities for bitwise operations.
* Hashing algorithms: Zobrist, binomial minimal perfect hash, Lehmer codes.

Built-in Tools
==============

Samurai provides several command-line tools usable with any built-in or
external engine supporting the UCI protocol:

* Interactive UCI shell and UCI service.
* Automatic opening-book construction tools using UTC trees.
* Benchmarking tools (including perft, divide, and round-robin tournaments).
* A command-line interface for playing against an engine.

Sample Games
============

This repository includes simple (and sometimes incomplete)
implementations for several games: chess, checkers, go, othello, oware,
and tic-tac-toe.

An implementation for using Samurai with GGP (General Game Playing) is
also included, serving as a reference for implementing and testing new
engines.

Building with Maven
===================

This project uses Maven for building and managing dependencies. Here's
how to get started:

Prerequisites:

* Java 11 or later
* Apache Maven

Build and Package:

1. Clone or download the repository.
2. Navigate to the project directory in your terminal.
3. Run ```mvn``` to build the project.

Native image builds with GraalVM
================================

GraalVM's Native Image allows you to compile your Java code ahead-of-time
(AOT) into a standalone executable, improving startup time and reducing
overall application size. Here's how to build a game as a native image:

Prerequisites:

* GraalVM 22 or later

Ensure you have GraalVM installed with the Native Image extension. Refer
to the GraalVM documentation for installation instructions:
https://www.graalvm.org/22.1/reference-manual/native-image/.

Building with Profile-Guided Optimizations (PGO):

PGO allows you to further optimize the native image by providing profile information about how the engine is typically used. This can lead to
significant performance improvements.

1. Clone or download the repository.
2. Navigate to the project directory in your terminal.
3. Run ```mvn -Poptimized``` to build the project.

Running Chess with Samurai Framework
====================================

The provided instructions successfully build the Samurai framework with
the sample game implementations. Here's how to interact with the Chess
engine using the built JAR file:

## Displaying Help

To see the general Chess engine options, run:

```
java -jar target/chess-1.2.0-SNAPSHOT-jar-with-dependencies.jar --help
```

This will display available options like ```--disturbance```, ```--roots```,
and ```--threshold``` for opening book management, along with commands
like ```book```, ```match```, ```service```, and ```shell```.

## Specific Command Help

To get help for individual commands like ```book```, use:

```
java -jar target/chess-1.2.0-SNAPSHOT-jar-with-dependencies.jar book --help
```

This will show options for ```query```, ```export```, and ```train```
related to opening book management.

## Starting UCI Service

To start the Chess engine in UCI mode, allowing external chess programs
to interact with it, run:

```
java -jar target/chess-1.2.0-SNAPSHOT-jar-with-dependencies.jar service
```

This will typically be used by other chess interfaces or tools.

## Interactive UCI Shell

To enter an interactive UCI shell where you can directly send UCI
commands to the engine, run:

```
java -jar target/chess-1.2.0-SNAPSHOT-jar-with-dependencies.jar shell
```

Within the shell, you can issue commands like ```ucinewgame```,
```position fen ...```, and ```go movetime 1000``` to interact with the
engine. Refer to the UCI protocol documentation for detailed commands
(https://www.chessprogramming.org/UCI).

Command Line Interface
======================

The engines built with the Samurai framework, offer a common set of
commands for interacting with the engine and managing its functionalities.
These commands provide a standardized way to perform actions like opening
book management, playing games, and engine testing. However, engines can
also implement their own custom commands beyond this core set.

## Book Management

* ```book query```: Queries the opening book database for a specific position.
* ```book export```: Exports the opening book database to a file.
* ```book train```: Automatically builds an opening book database.

## Engine Execution

* ```match```: Play a match against the engine on the command line.
* ```service```: Starts the engine in UCI mode, allowing external programs
  to control it.
* ```shell```: Provides an interactive UCI shell where you can directly send
  UCI commands to the engine.

## Game Suite Utilities

* ```suite show```: Plays pre-defined game suites on the board.
* ```suite random```: Generates random game suites for testing purposes.

## Engine Testing

* ```test battle```: Runs a tournament between multiple engines.
* ```test bench```: Benchmarks the engine's performance.
* ```test play```: Play the provided games without benchmarking
* ```test divide```: Analyzes the search tree by counting leaves at each child node.
* ```test perft```: Counts the total number of leaf nodes in the search tree
      up to a certain depth.

These commands provide a powerful toolkit for interacting with the
engines, allowing you to manage opening books, play games, test engine
performance, debug and analyze its search behavior.

Using External Engines
======================

While these commands are typically used with the built-in engines, Samurai
allows you to interact with external engines that implement a compatible
UCI service. This is achieved using the ```--command``` option.

## Example: Running GNU Chess in an interactive shell

For instance, if you have GNU Chess installed and want to use its engine
within the Samurai framework's shell, you could potentially execute:

```
java -jar target/chess-1.2.0-SNAPSHOT-jar-with-dependencies.jar shell --command="gnuchess --uci"
```

This instructs the framework to launch ```gnuchess``` with the ```--uci```
flag, enabling GNU Chess to act as a UCI service that the Samurai shell
can interact with.

Once the command executes, you'll enter the Samurai shell. Here, you can
interact with the GNU Chess engine directly using UCI commands. Within
the shell, type ```uci``` to initiate an interactive session with GNU
Chess. Type ```quit``` to end the session.

Now, you can issue various UCI commands to control the engine. Samurai
shell should display the board after each UCI command. Typing ```TAB```
will provide autocompletion suggestions for valid UCI commands. Some
built-in engines may provide additional custom UCI commands.

The Latest Version
==================

Information on the latest version of this software and its current
development can be found on https://github.com/joansalasoler/engines/

Licensing
=========

Please see the COPYING file.
