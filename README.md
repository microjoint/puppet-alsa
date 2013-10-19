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

The alsa module installs, configures, and manages the alsa packages.

##Module Description

The alsa module handles running alsa across a range of operating systems and
distributions.  Where possible we use the upstream alsa templates so that the
results closely match what you'd get if you modified the package default conf
files.

##Setup

###What alsa affects

* alsa utiles.
* alsa configuration file.

###Beginning with alsa

include '::alsa' is enough to get you up and running.  If you wish to pass in
parameters like which servers to use then you can use:

```puppet
class { '::alsa':
  servers => [ 'alsa1.corp.com', 'alsa2.corp.com' ],
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

###I just want to tweak the servers, nothing else.

```puppet
class { '::alsa':
  servers => [ 'alsa1.corp.com', 'alsa2.corp.com' ],
}
```

###I'd like to make sure I restrict who can connect as well.

```puppet
class { '::alsa':
  servers  => [ 'alsa1.corp.com', 'alsa2.corp.com' ],
  restrict => 'restrict 127.0.0.1',
}
```

###I'd like to opt out of having the service controlled, we use another tool for that.

```puppet
class { '::alsa':
  servers        => [ 'alsa1.corp.com', 'alsa2.corp.com' ],
  restrict       => 'restrict 127.0.0.1',
  manage_service => false,
}
```

###Looks great!  But I'd like a different template, we need to do something unique here.

```puppet
class { '::alsa':
  servers         => [ 'alsa1.corp.com', 'alsa2.corp.com' ],
  restrict        => 'restrict 127.0.0.1',
  manage_service  => false,
  config_template => 'different/module/custom.template.erb',
}
```

##Reference

###Classes

* alsa: Main class, includes all the rest.
* alsa::install: Handles the packages.
* alsa::config: Handles the configuration file.
* alsa::service: Handles the service.

###Parameters

The following parameters are available in the alsa module

####`autoupdate`

Deprecated: This parameter previously determined if the alsa module should be
automatically updated to the latest version available.  Replaced by package\_
ensure.

####`config`

This sets the file to write alsa configuration into.

####`config_template`

This determines which template puppet should use for the alsa configuration.

####`driftfile`

This sets the location of the driftfile for alsa.

####`keys_controlkey`

Which of the keys is used as the control key.

####`keys_enable`

Should the alsa keys functionality be enabled.

####`keys_file`

Location of the keys file.

####`keys_requestkey`

Which of the keys is used as the request key.

####`package_ensure`

This can be set to 'present' or 'latest' or a specific version to choose the
alsa package to be installed.

####`package_name`

This determines the name of the package to install.

####`panic`

This determines if alsa should 'panic' in the event of a very large clock skew.
We set this to false if you're on a virtual machine by default as they don't
do a great job with keeping time.

####`preferred_servers`

List of alsa servers to prefer.  Will append prefer for any server in this list
that also appears in the servers list.

####`restrict`

This sets the restrict options in the alsa configuration.

####`servers`

This selects the servers to use for alsa peers.

####`service_enable`

This determines if the service should be enabled at boot.

####`service_ensure`

This determines if the service should be running or not.

####`service_manage`

This selects if puppet should manage the service in the first place.

####`service_name`

This selects the name of the alsa service for puppet to manage.


##Limitations

This module has been built on and tested against Puppet 2.7 and higher.

The module has been tested on:

* RedHat Enterprise Linux 5/6
* Debian 6/7
* CentOS 5/6
* Ubuntu 12.04
* Gentoo
* Arch Linux
* FreeBSD

Testing on other platforms has been light and cannot be guaranteed. 

##Development

Puppet Labs modules on the Puppet Forge are open projects, and community
contributions are essential for keeping them great. We can’t access the
huge number of platforms and myriad of hardware, software, and deployment
configurations that Puppet is intended to serve.

We want to keep it as easy as possible to contribute changes so that our
modules work in your environment. There are a few guidelines that we need
contributors to follow so that we can have a chance of keeping on top of things.

You can read the complete module contribution guide [on the Puppet Labs wiki.](http://projects.puppetlabs.com/projects/module-site/wiki/Module_contributing)
