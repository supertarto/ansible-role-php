# Ansible PHP
[![CI](https://github.com/supertarto/ansible-role-php/actions/workflows/ci.yml/badge.svg)](https://github.com/supertarto/ansible-role-php/actions/workflows/ci.yml)


Install and configure PHP, for Debian, with Ansible. Tested with Apache. 

## Requirements

A web server (Apache, Nginx). Tested only with Apache. You can use supertarto.apache

## Tested plateforms
* Debian 11 (Bullseye)
* Debian 12 (Bookworm)
* Debian 13 (Trixie)

## Role Variables

List of packages instaled by the role. It's not yet possible to install php from source.
```yaml
php_packages:
  - "php{{php_default_version_debian}}"
```
The default version value is defined in the vars folder, based on the Debian version.

Name of the webserver daemon used by PHP. For example, apache2, httpd, nginx... Needed.
```yaml
php_webserver_daemon: "apache2"
```

PHP.ini variables. It's only those i use. You can define your own and edit the template.
```yaml
############################################################
# PHP.INI
# Instructions here: https://www.php.net/manual/fr/ini.php
############################################################

####################################
# Language Options
####################################

php_ini_precision: "14"
php_ini_output_buffering: "4096"

php_ini_disable_functions: []

#####################
# Resource Limits
#####################

php_ini_max_execution_time: "30"
php_ini_max_input_time: "60"
php_ini_memory_limit: "128M"

#############################
# Error handling and logging
#############################
php_ini_error_reporting: "E_ALL & ~E_DEPRECATED & ~E_STRICT"
php_ini_display_errors: "Off"
php_ini_display_startup_errors: "Off"

#####################
# Data Handling
#####################
php_ini_post_max_size: "25M"
php_ini_default_mimetype: "text/html"
php_ini_default_charset: "UTF-8"

#####################
# File Uploads
#####################
php_ini_file_uploads: "On"
php_ini_upload_max_filesize: "100M"
php_ini_max_file_uploads: "20"

#####################
# Fopen wrappers
#####################
php_ini_allow_url_fopen: "On"

#####################
# Module Settings
#####################
php_ini_date_timezone: "Europe/Paris"
```

## License
GPL V3.0
