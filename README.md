<img src="https://d3qt5vpr7p9rgn.cloudfront.net/wp-content/uploads/2013/08/easy-engine-logo-2-RS1.png" alt="EasyEngine Logo" align="right" />

[![Travis Build Status](https://travis-ci.org/mylivingweb/easyengine.svg "Travis Build Status")] (https://travis-ci.org/mylivingweb/easyengine)

easyengine (ee) is a linux shell-script collection, which makes it easy to manage your wordpress sites running on nginx web-server.

**EasyEngine CentOS currently supports:**

- CentOS 6.X

**This script will partially work for now**
- script adds REPL, NGINX, and REMI repos
- chkconfig for nginx, mysql, and php-fpm
- secures mysql install
- installs wordfence, ewww image optimizer, and jetpack

**things left to do**
- add iptables rules for 80,443 and potentially ssh 
- visit varnish caching


## Quick Start

```bash
curl -sL https://raw.githubusercontent.com/mylivingweb/easyengine/master/install.sh | sudo bash         # install easyengine
ee system install                     # install nginx, php-fpm, mysql, only run once
ee site create example.com --wp       # create example.com and install wordpress on it
```
## More Site Creation Commands

### Standard WordPress Sites

```bash
ee site create example.com --wp                  # install wordpress without any page caching
ee site create example.com --w3tc                # install wordpress with w3-total-cache plugin 
ee site create example.com --wpsc                # install wordpress with wp-super-cache plugin 
ee site create example.com --wpfc                # install wordpress + nginx fastcgi_cache
ee site disable example.com 					 # moves .conf file to directory and reloads nginx
ee site enable example.com						 # moves .conf file from directory to conf.d and reload nginx
```

### WordPress Multsite with subdirectory 

```bash
ee site create example.com --wpsubdir            # install wpmu-subdirectory without any page caching
ee site create example.com --wpsubdir --w3tc     # install wpmu-subdirectory with w3-total-cache plugin 
ee site create example.com --wpsubdir --wpsc     # install wpmu-subdirectory with wp-super-cache plugin 
ee site create example.com --wpsubdir --wpfc     # install wpmu-subdirectory + nginx fastcgi_cache
```

### WordPress Multsite with subdomain 

```bash
ee site create example.com --wpsubdom            # install wpmu-subdomain without any page caching
ee site create example.com --wpsubdom --w3tc     # install wpmu-subdomain with w3-total-cache plugin 
ee site create example.com --wpsubdom --wpsc     # install wpmu-subdomain with wp-super-cache plugin 
ee site create example.com --wpsubdom --wpfc     # install wpmu-subdomain + nginx fastcgi_cache
```

### Non-WordPress Sites
```bash
ee site create example.com --html     # create example.com for static/html sites
ee site create example.com --php      # create example.com with php support
ee site create example.com --mysql    # create example.com with php & mysql support
```

## Cheatsheet - Site creation


|                    |  Single Site  | 	Multisite w/ Subdir  |	Multisite w/ Subdom  |
|--------------------|---------------|-----------------------|-----------------------|
| **NO Cache**       |  	  --wp     |	    --wpsubdir       |	     --wpsubdom      |
| **WP Super Cache** |	  --wpsc     |	  --wpsubdir --wpsc  |  	--wpsubdom --wpsc  |
| **W3 Total Cache** |    --w3tc     |	  --wpsubdir --w3tc  |  	--wpsubdom --w3tc  |
| **Nginx cache**    |    --wpfc     |    --wpsubdir --wpfc  |  	--wpsubdom --wpfc  |


## Useful Links
- [Documentation] (http://rtcamp.com/easyengine/docs/) 
- [FAQ] (http://rtcamp.com/easyengine/faq/)
- [Conventions used] (http://rtcamp.com/wordpress-nginx/tutorials/conventions/)

