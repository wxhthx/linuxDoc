## Node.js is available from the NodeSource Debian and Ubuntu binary distributions repository (formerly Chris Lea's Launchpad PPA). Support for this repository, along with its scripts, can be found on GitHub at nodesource/distributions.

    NOTE: If you are using Ubuntu Precise or Debian Wheezy, you might want to read about running Node.js >= 4.x on older distros.
```Bash
curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
sudo apt-get install -y nodejs
```

Optional: install build tools

    To compile and install native addons from npm you may also need to install build tools:
```Bash
sudo apt-get install -y build-essential
```
this is the description content from nodejs website,however u have not access to use npm,so u have to do it like below:
```Bash
sudo apt-get install npm
```
(Note: The optional "nodejs-legacy" package from Debian helps prevent a conflict with the Amateur Packet Radio "Node" Program)
