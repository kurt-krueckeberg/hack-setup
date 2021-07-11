## FastCGI with Nginx

See [Makeing it work with nginx](https://docs.hhvm.com/hhvm/advanced-usage/fastCGI#using-fastcgi__making-it-work-with-nginx)

Note: This will send .hh and .php files to the HHVM fastcgi process. I may need to specify .hack, too?

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
