Gitian Wallet Build Script
================

This script was made by bitcoin core and this doc was made by mrmetech

Using gitian to compile wallets is a pain and that is why this script was made it just makes life easier.
We will be going over how to use it and stuff and things.


How to set it up
---------------------------------

To set it up you will want to clone the respository.

	git clone https://github.com/AnonymousDo/Helpico.git
	
Then do cd into the contrib folder.

	cd helpico/contrib
	
Now you will want to move the script to the same directory as the helpico folder as the Script will need to access the folder.

	cp gitian-build.sh ../..
	
Now that the script is in the write location cd back to the Directory you started in.

	cd ../..
	
These step is optional depending if the script already has run premissions 

	chmod +x gitian-build.sh
	
Last thing is to setup Gitian

	./gitian-build.sh --setup
	
	
How to run it
---------------------------------

To start off with there are two ways to set this up either with flags or by changing some of the defaults in the script 

	Usage: $scriptName [-c|u|v|b|s|B|o|h|j|m|] signer version
	Run this script from the directory containing the helpico, gitian-builder, gitian.sigs, and helpico-detached-sigs.
	Arguments:
	signer          GPG signer to sign each build assert file
	version        Version number, commit, or branch to build. If building a commit or branch, the -c option must be specified
	Options:
	-c|--commit    Indicate that the version argument is for a commit or branch
	-u|--url    Specify the URL of the repository. Default is https://github.com/helpicoofficial/helpico
	-v|--verify     Verify the gitian build
	-b|--build    Do a gitian build
	-s|--sign    Make signed binaries for Windows and Mac OSX
	-B|--buildsign    Build both signed and unsigned binaries
	-o|--os        Specify which Operating Systems the build is for. Default is lwx. l for linux, w for windows, x for osx, a for aarch64
	-j        Number of processes to use. Default 2
	-m        Memory to allocate in MiB. Default 2000
	--kvm           Use KVM instead of LXC
	--setup         Setup the gitian building environment. Uses KVM. If you want to use lxc, use the --lxc option. Only works on Debian-based systems (Ubuntu, Debian)
	--detach-sign   Create the assert file for detached signing. Will not commit anything.
	--no-commit     Do not commit anything to git
	-h|--help    Print this help message
	
Those are all the flags that there are.

or you can manually do it for example here are the defaults

	# What to do
	sign=false
	verify=false
	build=false

	# Systems to build
	linux=true
	windows=true
	osx=true

	# Other Basic variables
	SIGNER=
	VERSION=
	commit=false
	url=https://github.com/AnonymousDo/Helpico
	proc=2
	mem=2000
	
You can change it to what you need for long term like these

	# What to do
	sign=false
	verify=false
	build=false
	
change linux=false if you don't want to compile a linux wallet and mac wallet. And do do windows=true if you want it to compile windows wallets 

	# Systems to build
	linux=false
	windows=true
	osx=false

For signer you can do you gpg key so SIGNER=mrmetech and version the version of the wallet release you want to compile VERSION=1.3.2 for 
example then proc is the amount of cores you want to use and mem is ram or memory this is set in megabytes	
	
	# Other Basic variables
	SIGNER=
	VERSION=
	commit=false
	url=https://github.com/AnonymousDo/Helpico
	proc=2
	mem=2000











The maker of this is mrmetech

