## Creating a Hack Project

Make sure [composer](https://getcomposer.org/doc/00-intro.md#downloading-the-composer-executable) is installed.

See [Getting Started: Starting A Real Project](https://docs.hhvm.com/hack/getting-started/starting-a-real-project). I created **hack_proj**, a bash script that
performs the steps discussed in this link:

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

**vendor/bin/hh-autoload** should be run to update the ./vendor/autoload.hack file which maps your classes, functions, etc, to the correct **.hack** file.

