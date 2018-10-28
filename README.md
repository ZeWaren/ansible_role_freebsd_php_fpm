# ansible-freebsd-php-fpm

## Introduction
This role installs and configure `php-fpm` on FreeBSD.

## Variables

See [defaults/main.yml](defaults/main.yml) for the default values of each.

### php_version

Which version of PHP to install.

### php_fpm_remove_default_pool

Whether or not to delete the default pool that is created and installed by default by the port.

### php_fpm_conf

The location of the configuration file of php-fpm (usually `/usr/local/etc/php-fpm.conf`).

### php_fpm_d

Where the pool configuration files should be stored. (usually `/usr/local/etc/php-fpm.d`)

### php_fpm_service_name

The name of the rc service. (usually `php-fpm`)

### php_fpm_rc_var

The name of the rc var of the service. (usually `php_fpm_enable`)

### php_fpm_enabled

Should the service be enabled.

### php_fpm_started

Should the service be started.

### php_fpm_pool_defaults

The general configuration of the pools.

### php_fpm_pools

The configuration of each pool.

### php_fpm_modules

Which PHP modules should be installed and loaded.

### php_fpm_pecl_modules

Which PECL modules should be installed and loaded.

## Example

	php_version: 72
	php_fpm_pool_defaults:
	  pm: dynamic
	  pm.max_children: 50
	  pm.start_servers: 20
	  pm.min_spare_servers: 10
	  pm.max_spare_servers: 30
	php_fpm_pools:
	- 
	  name: example_com
	  user: example_com
	  group: example_com
	  listen: /var/run/phpfpm-example_com-directory.socket
	  listen.owner: example_com
	  listen.group: www
	  listen.mode: "0770"
	  php_admin_flag:
	    engine: on
	    register_globals: off
	    allow_call_time_pass_reference: off
	    expose_php: off
	    zend.ze1_compatibility_mode: off
	    register_long_arrays: off
	    display_errors: off
	    log_errors: on
	  php_admin_value:
	    session.cookie_lifetime: 0
	    max_execution_time: 300
	    memory_limit: 1024M
	    date.timezone: Europe/Paris
	    upload_max_filesize: 64M
	    post_max_size: 64M
	php_fpm_modules:
	  - session
	  - json
	  - hash
	  - ctype
	  - mcrypt
	  - curl
	  - gettext
	  - filter
	  - xml
	  - simplexml
	  - tokenizer
	  - gd
	  - mbstring
	  - iconv
	  - zlib
	  - openssl
	php_fpm_pecl_modules:
	  - redis

## Dependencies

None.

## Licence

BSD

## Author

[Erwan Martin](https://zewaren.net/)
