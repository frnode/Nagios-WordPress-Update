Nagios-WordPress-Update
===============

A Nagios plugin to check for WordPress version updates on a remote server without the use of NRPE.

How to use:

- Upload wp-version.php to your WordPress root installation
- Include the IP address of your Nagios installation in the script
- Copy "check_wp" to your Nagios plugins folder. For me, it's on /usr/lib64/nagios/plugins
- Create a service command template
- Create a service check on your host

__Command Template__

	define command{
        command_name    check_wp
        command_line    $USER1$/check_wp $ARG1$
	}


__Service Check__

	define service {
        max_check_attempts      8
        host_name               wordpress
        service_description     Wordpress_comments
        check_command           check_wp!http://example.com/wp-version.php
        check_interval          5
        check_period            24x7
	}

Inspired by check\_wp\_version by @hteske. Original [here](http://exchange.nagios.org/directory/Plugins/CMS-and-Blog-Software/Wordpress/check_wp_version/details)

Version modified by @frnode to be compatible with [nagios-wp-check-comments](https://github.com/frnode/nagios-wp-check-comments)
