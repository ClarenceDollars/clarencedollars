   # Clarence Dollars  [ CLAN ]



![ClarenceDollars](https://vignette.wikia.nocookie.net/clarence-la/images/b/b5/Clarence%27s_Millions_-_Storyboard_1.gif/revision/latest?cb=20140603193541&path-prefix=es)

[![Build Status](https://travis-ci.org/dogecoin/dogecoin.svg?branch=1.7-dev)](https://travis-ci.org/dogecoin/dogecoin)

## What are Clarence Dollars?
Clarence Dollars are a cryptocurrency like Bitcoin, although it does not use SHA256 as its proof of work (POW). Taking development cues from Litecoin and Dogecoin, Clarence Dollars currently employs a simplified variant of scrypt.


#### Branches
There are 3 types of branches in this repository:

- **master:** Stable, contains the latest version of the latest *major.minor* release.
- **maintenance:** Stable, contains the latest version of previous releases, which are still under active maintenance. Format: ```<version>-maint```
- **development:** Unstable, contains new code for planned releases. Format: ```<version>-dev```

*Master and maintenance branches are exclusively mutable by release. Planned releases will always have a development branch and pull requests should be submitted against those. Maintenance branches are there for* ***bug fixes only,*** *please submit new features against the development branch with the highest version.*

## Very Much Frequently Asked Questions

### How many Clarence Dollars can exist? 
Early 2020 (approximately a year and a half after release) there will be approximately 100,000,000,000 Clarence Dollars.
Each subsequent block will grant 10,000 CLAN to encourage miners to continue to secure the network and make up for lost wallets on hard drives/phones/lost encryption passwords/etc.

### How to get CLAN?!
Clarence Dollars uses a simplified variant of the scrypt key derivation function as its proof of work with a target time of one minute per block and difficulty readjustment after every block. The block rewards are fixed and halve every 100,000 blocks. Starting with the 600,000th block, a permanent reward of 10,000 CLAN per block will be paid. 

### Make clarencedollarsd/clarencedollars-cli/clarencedollars-qt

  The following are developer notes on how to build Clarence Dollars on your native platform. They are not complete guides, but include notes on the necessary libraries, compile flags, etc.

  - [OSX Build Notes](doc/build-osx.md)
  - [Unix Build Notes](doc/build-unix.md)
  - [Windows Build Notes](doc/build-msw.md)

### Such ports
RPC 22555
P2P 22556

Translations
------------

Changes to translations, as well as new translations, can be submitted to
[Bitcoin Core's Transifex page](https://www.transifex.com/projects/p/bitcoin/).

Periodically the translations are pulled from Transifex and merged into the git repository. See the
[translation process](doc/translation_process.md) for details on how this works.

If the changes are Clarence Dollar specific, they can be submitted as pull requests against this repository.
If it is a general translation, consider submitting it through upstream, as we will pull these changes later on.

Development tips and tricks
---------------------------

**compiling for debugging**

Run configure with the --enable-debug option, then make. Or run configure with
CXXFLAGS="-g -ggdb -O0" or whatever debug flags you need.

**debug.log**

If the code is behaving strangely, take a look in the debug.log file in the data directory;
error and debugging messages are written there.

The -debug=... command-line option controls debugging; running with just -debug will turn
on all categories (and give you a very large debug.log file).

The Qt code routes qDebug() output to debug.log under category "qt": run with -debug=qt
to see it.

**testnet and regtest modes**

Run with the -testnet option to run with "play dogecoins" on the test network, if you
are testing multi-machine code that needs to operate across the internet.

If you are testing something that can run on one machine, run with the -regtest option.
In regression test mode, blocks can be created on-demand; see qa/rpc-tests/ for tests
that run in -regtest mode.

**DEBUG_LOCKORDER**

CLAN is a multithreaded application, and deadlocks or other multithreading bugs
can be very difficult to track down. Compiling with -DDEBUG_LOCKORDER (configure
CXXFLAGS="-DDEBUG_LOCKORDER -g") inserts run-time checks to keep track of which locks
are held, and adds warnings to the debug.log file if inconsistencies are detected.
