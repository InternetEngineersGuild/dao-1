# The DAO framework

--

**IMPORTANT UPDATE:** Many new interesting libraries are going into production. One of the most interesting-looking ones is BoardRoom (http://boardroom.to/). This looks like it will be very good, and I am very excited to get to try it myself.

If that becomes the case, my code from now on will be centered around modules for that library, and these type of libraries will be around for research purposes and for providing examples. More time will be spent on tutorials and such, and to frame specific code and contract, and complement them with charts and written material (focus will be 100% on education).

--

This is the a light-weight framework for modular systems of [Ethereum](https://ethereum.org/) contracts. It is meant to be used with Ethereum, or other chains that supports Ethereum contracts. It will get a better name.

The contracts are written in the [Solidity](http://solidity.readthedocs.org/en/latest/index.html) language. The purpose of this library as of now is to act as a template for extending, or just as an example of how to write Solidity contracts. This is a **contracts-only library**, but there are some javascript utilities for deploying and testing.

The architecture is a new iteration of the architecture that I outlined in [these tutorials](https://docs.erisindustries.com/tutorials/solidity/solidity-1/), and that I had implemented in a now outdated LLL DApp named [The People's Republic of Doug](https://github.com/androlo/EthereumContracts).  

NOTE: Ethereum is still experimental, and so is this code. Using this on a chain where Ether has real value, or in any form of production environment is **not** recommended.

## Table of Content

- [Getting Started](#getting-started)
- [Dependencies and Tools](#dependencies-and-tools)
- [Building, Testing and Documentation](#btd)
- [Structure](#structure)
- [Javascript Utilities](#javascript-utilities)
- [DAO framework?](#dao-framework)
- [Troubleshooting](#troubleshooting)
- [Business](#business)
- [Licence](#licence)

## Getting started

A good demo will become available during February.

There are [Tutorials](./docs/Tutorials.md). 

There are examples in the [examples folder](./examples/README.md).

Each module has a README file that explains what it does. They are all referenced in the [Structure](#structure) section of this document.

HTML documentation for all the contracts can be found at http://smartcontractproduction.github.io/dao-contracts.

HTML documenttion for the javascript can be found at http://smartcontractproduction.github.io/dao-javascript

To understand how systems are kept intact, maybe take a look at the document on [Permission Analysis](./docs/Permission_Analysis.md).

## Dependencies and Tools

The tools are only tested on 64 bit Ubuntu 14.04+

[node.js](https://nodejs.org/en/) is a requirement for most of the scripts. The scripts are based on the official javascript APIs, such as the [Ethereum web3.js library](https://github.com/ethereum/web3.js), and are used for deployment and testing etc.

Command-line [Gulp](http://gulpjs.com/) is optional, but has tasks for building and deploying.

You need [solc](https://github.com/ethereum/solidity) on your path to build contracts (latest dev).

You need [NaturalDocs](http://www.naturaldocs.org/) and [jsdoc](http://usejsdoc.org/) on your path to build html documentation.

**Formal proofs**

You need [why3](http://why3.lri.fr/) (latest release).

Solidity to why3 is still experimental, and is not required for normal usage.

<a name="btd">
## Building, Testing, and Documentation

Building, testing and doc generation can be done for each module separately. Check the README in each folder for instructions. It can also be done for the entire framework at once using Gulp.

NOTE: This requires that the dependencies are in place.

##### Building

NOTE: You need `solc` on path. If this fails it will mess up the build folders, so you need to download again, or `git stash`.

Gulp: `$ gulp build:all`

## Structure

These are the different parts of the framework.

**Modules**

- [dao-core](https://github.com/smartcontractproduction/dao/blob/master/dao-core/README.md) - core contracts.
- [dao-currency](https://github.com/smartcontractproduction/dao/blob/master/dao-currency/README.md) - a basic sub-currency.
- [dao-users](https://github.com/smartcontractproduction/dao/blob/master/dao-users/README.md) - some basic user management.
- [dao-votes](https://github.com/smartcontractproduction/dao/blob/master/dao-votes/README.md) - contracts for public voting.

**Utilities**

- [dao-stl](https://github.com/smartcontractproduction/dao/blob/master/dao-stl/README.md) - shared, standard contracts.

## Javascript Utilities

There are a number of utilities that comes with this library, even though it is a contracts-only library. These will be documented and tested later, probably at `0.3.0`

## DAO framework

Yes, this is a framework for DAOs (Decentralized Autonomous Organizations), although one could argue that it is not, because if there are administrator accounts then the organization is not really autonomous. This is correct, but it is *possible* to create autonomous systems, or those that are "somewhat autonomous" (through the use of voting and other mechanisms).

It really works like Ethereum contracts. Ethereum contracts are often called smart-contracts even though they don't have to be smart, and they don't have to be [legal] contracts; the Ethereum protocol can't be used to check if that is indeed what they are. Similarly, the DAO framework lets you create DAOs, but they don't have to be distributed, autonomous, or organizations. You can create a fully managed single user system and deploy it on an offline block-chain node, nothing in this framework will prevent you from doing that, but if you want to create a DAO you can do that too.

## Troubleshooting

This library is open source only to show some working Solidity code, because there is not a lot of resources around. I look into issues, but there's no official support or feature-request system. 

This library is only officially supported on 64 bit Ubuntu 14.04+, although it should work on recent OSX versions. I will look into building on Windows when I have time.

**I don't know what any of this is**

https://ethereum.org/

**I don't know how to read the contract code**

http://solidity.readthedocs.org/en/latest/index.html

**I understand Solidity syntax, but not the purpose of the contracts**

This is probably because this is a framework, and much of the code are architectural elements. Also there is lots of imports and such. To understand it, you might want to read the overview section of the [User Manual](./docs/Manual.md#overview), and the README for each component. There are explanations and diagrams that shows how it works. The [Permission Analysis](./docs/Permission_Analysis.md) is a good read as well.

If you have checked it out and still don't get it, then it's probably because the documentation is not clear. It will improve over time.

**I understand what the code does, but I don't understand why I should use it**

The framework is useful because it is fairly simple, but has most of the fundamentals like permissions structures, registries, tests, docs, etc. The quality requirements both in terms of code and design are very high. It pushes the limits on what you can do with Ethereum contracts and Solidity. Finally, it is essentially a more well-engineered version of a framework that has been worked on since before Solidity existed, so there's been time to find mistakes, and to correct them.

The bad thing is it's a framework that I (the author) made to use in my own projects, which have higher priority then the framework itself. This means that development can be slow at times, and support might not be good.

Maybe it's good for someone, maybe not.

**I can't build the contracts**

This is normally because you don't have [solc](https://github.com/ethereum/solidity) installed and on your path. This library only works with a local C++ version, because building everything with the bytecode optimizer on can take very long (several minutes).

**I can't test the contracts**

This is normally because the contract build folders has been tampered with, or because sol-unit can't be installed. The reason for sol-unit failure could be missing dependencies. sol-unit uses javascript ethereum which depends on C/C++ libraries, which you may not be able to build. Among other things it requires make, g++ and gmp (`libgmp3-dev`).

## Business

**Hiring Me**

I work with Ethereum contracts and various different block-chain clients, and is sometimes available for projects.

To contact me, send a personal message on linkedin: https://www.linkedin.com/in/andreas-olofsson-69465ba4

**Me Hiring**

I'm not hiring as of right now.

## Licence

The entire framework is licensed under MIT.
