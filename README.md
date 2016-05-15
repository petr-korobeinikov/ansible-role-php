[![Build Status](https://travis-ci.org/pkorobeinikov/ansible-role-php.svg?branch=master)](https://travis-ci.org/pkorobeinikov/ansible-role-php)

ansible-role-php
================

PHP installation.

Requirements
------------

You must provide your own `php-fpm.ini.j2`, `php-cli.ini.j2 and `php-fpm.conf` templates.

Role Variables
--------------

* `php_version` is a php version number, e.g. `7.0`.
* `php_package_version` is an exact package version.
* `php_modules` is an array of required modules.
* `php_config_templates` is an array of config file templates.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      roles:
        # Install php7.0
        - role: ansible-role-php
          php_version: 7.0
          php_package_version: 7.0.6-9+donate.sury.org~trusty+2
          php_modules:
            - fpm
            - cli
            - xml
          php_config_templates:
            - { src: php/7.0/php.cli.ini.j2, dest: /etc/php/7.0/cli/php.ini }
            - { src: php/7.0/php.fpm.ini.j2, dest: /etc/php/7.0/fpm/php.ini }
            - { src: php/7.0/www.conf.j2, dest: /etc/php/7.0/fpm/pool.d/www.conf }

        # Install php5.6
        - role: ansible-role-php
          php_version: 5.6
          php_package_version: 5.6.21-7+donate.sury.org~trusty+1
          php_modules:
            - fpm
            - cli
            - xml
          php_config_templates:
            - { src: php/5.6/php.cli.ini.j2, dest: /etc/php/5.6/cli/php.ini }
            - { src: php/5.6/php.fpm.ini.j2, dest: /etc/php/5.6/fpm/php.ini }
            - { src: php/5.6/www.conf.j2, dest: /etc/php/5.6/fpm/pool.d/www.conf }

License
-------

BSD, MIT
