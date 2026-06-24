# cmdLookup
A Linux (command line) command lookup tool for commands using command-not-found.com.

# installation

To install, run:

curl -1sLf 'https://dl.cloudsmith.io/public/pixeleyesd/cmdlookup/setup.deb.sh' | sudo -E bash

sudo apt install cmdlookup

if that doesn't work but you are running a debian or ubuntu based distro, try

curl -1sLf 'https://dl.cloudsmith.io/public/pixeleyesd/cmdlookup/setup.deb.sh' | distro=ubuntu version=24.04 codename=noble sudo -E bash

sudo apt install cmdlookup