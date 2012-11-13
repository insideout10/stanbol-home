stanbol-home
============

This repository is a clean template to create a start-up folder for Apache Stanbol.

This are the repository contents:
```
 + /opt/stanbol/
    + bin/
      - stanbol
    + etc/
      - stanbol.conf
    + var/
      + run/
        - 1/
```

# Installation

Checkout the repository in `/opt/stanbol`:
```sh
git clone https://github.com/insideout10/stanbol-home.git /opt/stanbol
```

## bin/stanbol

The file `bin/stanbol` is an init.d compatible file to automatically start-up Apache Stanbol at boot. Configure it as follows:
```sh
cd /etc/init.d
ln -s /opt/stanbol/bin/stanbol
update-rc.d stanbol defaults
```

The file should work out-of-the-box (assuming that Apache Stanbol is installed in `/opt/stanbol/bin/stable`) and is configured to use 1GB of memory for Apache Stanbol.

Further tunings can be done by editing the file.

## etc/stanbol.conf

The file `etc/stanbol.conf` is an *apache2* configuration file to configure a reverse proxy on Apache Stanbol and expose only the desired services.

Before installing the file it is **required** to update the *stanbol* server address with your server address by editing the file.

The file can be installed as follows:
```sh
cd /etc/apache2/sites-available
ln -s /opt/stanbol/etc/stanbol.conf
a2ensite stanbol.conf
service apache2 restart
```

