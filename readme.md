What is it?
===========

This repository contains a framework for implementing zero-sum game engines and some reference games implemented with it.

Samurai is a generic framework for implementing search engines for zero-sum games. It provides a variety of algorithms and tools that can be used to develop engines for a wide range of games, including:

* UCI protocol support for any game.
* Base open-book implementation.
* Search algorithms: UCT, Negamax, Monte-Carlo, etc.
* Generic EGTB implementation.
* Generic transposition table implementation.
* Generic automatic opening-book generator.
* Position and move representation utilities.
* Utilities for bitwise operations.
* Hashing algorithms: Zobrist, binomial minimal perfect hash, Lehmer codes.

Some of the command-line tools provided by Samurai, that can be used with any built-in or external engine that implements the UCI protocol:

* Interactive UCI shell and UCI service.
* Automatic opening-book construction tools using UTC trees.
* Benchmarking tools (including perft, divide, and round-robin tournaments).
* A command-line interface for playing against an engine.

This repository also includes simple and sometimes incomplete implementations for some games, including chess, checkers, go, othello, oware, and tic-tac-toe.

In addition, it includes an implementation for using the framework with GGP (General Game Playing) that can be used as a reference for implementing new engines and test their implementations.

The Latest Version
==================

Information on the latest version of this software and its current
development can be found on https://github.com/joansalasoler/engines/

Licensing
=========

Please see the COPYING file.
