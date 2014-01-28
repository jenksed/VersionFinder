VersionFinder
=============

VersionFinder is a script that has the ability to scan multiple websites, normally in a shared hosting environment, and report outdated version of common CMS installs.


Usage
=============


```
Usage: ./versionfinder [OPTION] [--user username]

Scan server for known CMS versions and report what is found

	--outdated
		Returns only outdated packages, does not print headings
	--report
		Removes coloring format for easy export to file using > filename
	--csv
		Prints output in CSV format.
	--user <username>
		Scans only user's account, use quotes for a providing a list of users
	--directory <directory>
		Scans only a specific directory, used quotes for providing a list of directories
	--sigs
		Print current list of program versions
```

Quick installation
=============

You can quickly install the latest version of version finder using wget:

```
mkdir -p /root/bin/
wget https://raw.github.com/JamesDooley/VersionFinder/master/versionfinder -O /root/bin/versionfinder
chmod 700 /root/bin/versionfinder
```

Note about EOL packages
=============

For the most part any major version of a CMS package, that is no longer available for easy download from a webside, will be considered End Of Life.  This includes packages that may still be updated, the logic is that if it is not easy to find an update most users will not bother to update the software.  Exceptions to this may be allowed if updates can be done through the admin interface for a package.


Note about packages with multiple signatures
=============

Several packages, such as Joomla, have multiple signatures to handle either architecture changes or to simplify support for multiple still supported major / minor releases.


Note about cPanel support
=============

Version finder was mainly designed with cPanel support in mind.  It should automatically detect all accounts on the server and scan all of the proper directories related to the account.  The user option can be used to scan specific users, likewise the directory option can be used to scan a specific directory.


Note about Plesk support
=============

Plesk support was added recently, but has not been as throughly tested as cPanel.  All domains listed in /var/www/vhosts should be automatically scanned by the script.  The user option can be used to scan specific users in /var/www/vhosts, likewise the directory option can be used to scan a specific directory.


Note about other systems / vanilla LAMP
=============

There is the beginnings of code to pull information directly from apache / nginx to get a list of all sites to scan, this code is not finished and will take some work to complete on my end. In the mean time you can still use this script by specifying the specific directory you want to scan. If all of the sites exist in a specific parent directory you can scan that directory like so:

 versionfinder --directory /home
