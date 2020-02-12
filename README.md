# apache2-ssl-config

    $ sudo a2enmod ssl

    $ grep -nwr . -e 10443
    ./sites-available/default-ssl.conf:3:	<VirtualHost _default_:10443>
    ./ports.conf:9:	Listen 10443
    ./ports.conf:13:	Listen 10443
    
    $ sudo vi ./sites-available/default-ssl.conf
    $ sudo vi ./ports.conf
    
    $ cd /etc/apache2/sites-enabled
    $ ls -l
    total 0
    lrwxrwxrwx 1 root root 35 Oct 22 10:43 000-default.conf -> ../sites-available/000-default.conf
    lrwxrwxrwx 1 root root 35 Feb 12 15:14 default-ssl.conf -> ../sites-available/default-ssl.conf
    
    $ cd /etc/apache2/mods-enabled
    $ $ ls -l ssl*
    lrwxrwxrwx 1 root root 26 Feb 12 15:52 ssl.conf -> ../mods-available/ssl.conf
    lrwxrwxrwx 1 root root 26 Feb 12 15:52 ssl.load -> ../mods-available/ssl.load
    
    $ cd /etc/apache2/ssl
    $ ls
    ca_bundle.crt  certificate.crt  private.key
    
    $ cd /etc/apache2/sites-available
    $ vi default-ssl.conf
    ...
                SSLCertificateFile      /etc/apache2/ssl/certificate.crt
                SSLCertificateKeyFile   /etc/apache2/ssl/private.key
    ...
    
    $ service apache2 restart
    
![](https://github.com/Charles-Hsu/apache2-ssl-config/edit/master/apache2-https-10443.png)
    
    
    
    
