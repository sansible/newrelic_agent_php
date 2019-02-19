# newrelic_agent_php

Master: [![Build Status](https://travis-ci.org/sansible/newrelic_agent_php.svg?branch=master)](https://travis-ci.org/sansible/newrelic_agent_php)
Develop: [![Build Status](https://travis-ci.org/sansible/newrelic_agent_php.svg?branch=develop)](https://travis-ci.org/sansible/newrelic_agent_php)

* [Installation and Dependencies](#installation-and-dependencies)
* [Tags](#tags)
* [Examples](#examples)

Installs New Relic's PHP agent and configures an INI file with symlinks
to this file to enable it. Comes with default settings that setup license key,
log levels, app name and extension location.

## Installation and Dependencies

To install run `ansible-galaxy install sansible.newrelic_agent_php` or add this to your
`roles.yml`.

```YAML
- name: sansible.newrelic_agent_php
  version: v1.0.x
```

and run `ansible-galaxy install -p ./roles -r roles.yml`


## Tags

This role uses tags: **build** and **configure**

* `build` - Installs Newrelic PHP agent
* `configure` - Configures Newrelic PHP agent


## Examples

Enable default PHP7.3 agent:

```YAML
- name: Install and configure newrelic
  hosts: "somehost"

  roles:
    - role: sansible.newrelic_agent_php
      sansible_newrelic_agent_php_appname: some-php7.3-app
      sansible_newrelic_agent_php_license_key: 123456789123456789123456789123456789
```

Configure custom ini file settings:

```YAML
- name: Install and configure newrelic
  hosts: "somehost"

  roles:
    - role: sansible.newrelic_agent_php
      sansible_newrelic_agent_php_appname: some-php7.3-app
      sansible_newrelic_agent_php_ini_config:
        - option: newrelic.distributed_tracing_enabled
          section: newrelic
          value: "true"
      sansible_newrelic_agent_php_license_key: 123456789123456789123456789123456789
```

Enable agent for a different version of PHP:

```YAML
- name: Install and configure newrelic
  hosts: "somehost"

  roles:
    - role: sansible.newrelic
      sansible_newrelic_agent_php_appname: some-php7.2-app
      sansible_newrelic_agent_php_ini_paths_base:  /etc/php/7.2/mods-available/newrelic.ini
      sansible_newrelic_agent_php_ini_paths_links:
      - /etc/php/7.2/fpm/conf.d/20-newrelic.ini
      - /etc/php/7.2/cli/conf.d/20-newrelic.ini
      sansible_newrelic_agent_php_license_key: 123456789123456789123456789123456789
```

## The start_on_boot flag

The start_on_boot flag will start the agent and write any required config files, executed via the configure tag. 
This tag can be used for activating an agent on a per environment basis, allowing the agent to be 
installed into a base image and then activated at run time.
