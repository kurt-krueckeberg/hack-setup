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
