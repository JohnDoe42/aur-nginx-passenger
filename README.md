# Introduction

This is the [PKGBUILD](https://wiki.archlinux.org/index.php/PKGBUILD) and
related source files to build [nginx](http://nginx.org/) with support for
[Phusion Passenger](https://www.phusionpassenger.com/) on
[Arch Linux](https://www.archlinux.org).

# Instructions

What, you wanted step-by-step install instructions?
[This package](https://aur.archlinux.org/packages/netbeans-php/) is available from
the [AUR](https://aur.archlinux.org/). You can install it by using the official
method for installing unsupported packages, which is exhaustively described in
the [Arch User Repository](https://wiki.archlinux.org/index.php/Arch_User_Repository) wiki
article.

# Configuration

Once you've installed this package, nginx needs to be configured to enable passenger.
Here's an example of /etc/nginx/nginx.conf:

	http {
		passenger_root /usr/lib/passenger;
		passenger_ruby /usr/bin/ruby;
		...

		server {
			listen 80;
			server_name www.example.com;
			root /srv/http/example/public; # <-- be sure to point to 'public'!
			passenger_enabled on;
		}

		...
	}