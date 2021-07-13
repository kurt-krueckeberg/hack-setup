## Building and Installing from Source

From [Installation: Building From Source](https://docs.hhvm.com/hhvm/installation/building-from-source):

1. Enable **src** entry in /etc/apt/sources.list.d/blah-blah-hhvm.list
2. Get build dependencies, clone repository, make and install:

    sudo apt update &&  apt-get build-dep hhvm-nightly
    git clone git://github.com/facebook/hhvm.git
    cd hhvm
    git submodule update --init --recursive
    cmake -DMYSQL_UNIX_SOCK_ADDR=/var/run/mysqld/mysqld.sock .
    make -j  4
    sudo make install

HHVM and related binaries are installed in /usr/local/bin.

Note: The hhvm server/daemon executes .hh and .php files. The .hh file must begin with "<?hh", and their subdir must contain **.hhconfig**.

## Running as Proxygen Server

The built-in HHVM proxygen server is the most efficient way to run hhvm and can be started from CLI:

    hhvm -m server -p 8080

or 

    hhvm -m server -d hhvm.server.port=8080

The default root source directory for your program .php and .hh files will be the current directory from where you launched the hhvm command. A different root can be specified 

    hhvm -m server -d hhvm.server.port=8080  -d hhvm.server.source_root=/home/kurt/temp

Client access is from **localhost:8080/index.php** or **localhost:8080/index.hh**, with index.php or index.hh residing in /home/kurt/temp.

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

TEST:

**-p 8080** is really equivalent to just **-d hhvm.server.port=8080**. Since the **-m server** parametert must be specified, and its use implies the server type is proxygen and the default source_root is **./**, explicitly specifying **d hhvm.server.type=proxygen -d hhvm.server.source_root=./** is redundant and therefore confusing to a new user.
