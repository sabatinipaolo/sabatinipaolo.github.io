        sudo apt install mariadb-server

        sudo mariadb-secure-installation

NOTE: RUNNING ALL ....

        Enter current password for root (enter for none): root
        OK, successfully used password, moving on...

        Setting the root password or using the unix_socket ...
        You already have your root account protected, so you can safely answer 'n'.

        Switch to unix_socket authentication [Y/n] n
        ... skipping.

        You already have your root account protected, so you can safely answer 'n'.

        Change the root password? [Y/n] n
        ... skipping.

        By default, a MariaDB installation has an anonymous user, ...

        Remove anonymous users? [Y/n] y
        ... Success!

        Normally, root should only be allowed to connect from 'localhost'...
        Disallow root login remotely? [Y/n] y
        ... Success!

        By default, MariaDB comes with a database named 'test' ...

        Remove test database and access to it? [Y/n] y
        - Dropping test database...
        ... Success!
        - Removing privileges on test database...
        ... Success!

        Reloading the privilege tables will ensure that all changes made so far
        will take effect immediately.

        Reload privilege tables now? [Y/n] y
        ... Success!

        Cleaning up...

        ...

        Thanks for using MariaDB!




PHP #########################à

sudo apt install php libapache2-mod-php php-mysql php-cgi php-fpm php-cli php-curl php-gd php-imap php-mbstring php-pear php-intl php-apcu php-common php-bcmath php-xml php-zip

    [fatto quando setup di osticket]

sudo phpenmod imap
sudo service apache2 restart

    [fatto quando post-setup di osticket]
sudo apt install php-zip
sudo phpenmod zip
sudo service apache2 restart


VSFTP ###########################


sudo nano /etc/vsftpd.conf

    # Uncomment this to enable any form of FTP write command.
    write_enable=YES

    # Default umask for local users is 077. You may wish to change this to 022,
    # if your users expect that (022 is used by most other ftpd's)
    local_umask=022

sudo systemctl restart vsftpd

OSTICKET #######################

    creazione del database per osticket

mysql -u root -p


CREATE DATABASE ostDB;

CREATE USER 'ostdbuser'@'localhost' IDENTIFIED BY 'ostdbuser' ;
grant all privileges on ostDB.* to 'ostdbuser'@'localhost';

flush privileges;

exit


    #cambiato proprietario di var/www/html in user
sudo chown user:user /var/www/html

    #rinominare index.html in index.html.old

mv /var/www/html/index.html /var/www/html/index.html.original

    scaricare osticket dal sito , dezipparla ,
    e upload con ftp della dir upload in web root


    dal server:

cp include/ost-sampleconfig.php include/ost-config.php

    #setup

ostadmin/ostadmin






