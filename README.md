## Building from Source

See [Installation: Building From Source](https://docs.hhvm.com/hhvm/installation/building-from-source). You have to enable the *src* line in in the /etc/apt/sources.list.d/blah-blah-hhvm.list

    sudo apt update &&  apt-get build-dep hhvm-nightly
    git clone git://github.com/facebook/hhvm.git
    cd hhvm
    git submodule update --init --recursive
    cmake -DMYSQL_UNIX_SOCK_ADDR=/var/run/mysqld/mysqld.sock .
    make -j  4
    sudo make install

It is installed into /usr/local/bin.

Note: The hhvm server/daemon executes .hh (that begin with <?hh ) and .php files.

## Running as a Daemon

## Running HHVM at System Startup


## Creating a Hack Project


See [Getting Started: Starting A Real Project](https://docs.hhvm.com/hack/getting-started/starting-a-real-project). The basic setup found in **hack_proj** bash script does:

    $ curl https://raw.githubusercontent.com/hhvm/hhast/master/.hhconfig > .hhconfig
    $ mkdir bin src tests
    
    $ cat > hh_autoload.json
    {
      "roots": [
        "src/"
      ],
      "devRoots": [
        "tests/"
      ],
      "devFailureHandler": "Facebook\\AutoloadMap\\HHClientFallbackHandler"
    }
    
    $ composer require hhvm/hsl hhvm/hhvm-autoload
    $ composer require --dev hhvm/hhast hhvm/hacktest facebook/fbexpect

    cat > hhast-lint.json
    {
      "roots": [ "bin/", "src/", "tests/" ],
      "builtinLinters": "all"
    }

See **hack-proj** bash script. 

**vendor/bin/hh-autoload** should be run to update the ./vendor/autload.hack file that maps your classes, functions, etc, to the **.hack** file in which they are reside.

RESUME here:https://docs.hhvm.com/hack/getting-started/starting-a-real-project
