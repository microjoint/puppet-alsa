#alsa

####Table of Contents

1. [Overview](#overview)
2. [Module Description - What the module does and why it is useful](#module-description)
3. [Setup - The basics of getting started with alsa](#setup)
    * [What alsa affects](#what-alsa-affects)
    * [Setup requirements](#setup-requirements)
    * [Beginning with alsa](#beginning-with-alsa)
4. [Usage - Configuration options and additional functionality](#usage)
5. [Reference - An under-the-hood peek at what the module is doing and how](#reference)
5. [Limitations - OS compatibility, etc.](#limitations)
6. [Development - Guide for contributing to the module](#development)

##Overview

The alsa module installs the alsa utilities package.

##Module Description

The alsa module handles installing alsa across a range of operating systems and
distributions.  

##Setup

###What alsa affects

* alsa utilities.

###Beginning with alsa

include '::alsa' is enough to get you up and running. 

```puppet
class { '::alsa':
}
```

##Usage

All interaction with the alsa module can do be done through the main alsa class.
This means you can simply toggle the options in the alsa class to get at the
full functionality.

###I just want alsa, what's the minimum I need?

```puppet
include '::alsa'
```

###There's currently no further options

##Reference

###Classes

* alsa: Main class, includes all the rest.
* alsa::install: Handles the packages.

###Parameters

None

##Limitations

This module has been built on and tested against Puppet 3.3 and higher.

The module has been tested on:

* Arch Linux

Testing on other platforms has been light and cannot be guaranteed. 
