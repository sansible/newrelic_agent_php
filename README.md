# newrelic_integration_php

Master: [![Build Status](https://travis-ci.org/sansible/newrelic_integration_php.svg?branch=master)](https://travis-ci.org/sansible/newrelic_integration_php)
Develop: [![Build Status](https://travis-ci.org/sansible/newrelic_integration_php.svg?branch=develop)](https://travis-ci.org/sansible/newrelic_integration_php)

* [Installation and Dependencies](#installation-and-dependencies)
* [Tags](#tags)
* [Examples](#examples)

This role ...


## Installation and Dependencies

To install run `ansible-galaxy install sansible.newrelic_integration_php` or add this to your
`roles.yml`.

```YAML
- name: sansible.newrelic_integration_php
  version: v1.0
```

and run `ansible-galaxy install -p ./roles -r roles.yml`


## Tags

This role uses tags: **build** and **configure**

* `build` - Installs ...
* `configure` - Configures ...


## Examples

Simply include role in your playbook

```YAML
- name: Install and Configure newrelic_integration_php
  hosts: somehost

  roles:
    - role: sansible.newrelic_integration_php
```
