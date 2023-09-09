# infotrixs
WordPress site over AWS using RDS
Sure, I can help you with that. Here is a possible README file for your GitHub project that uses the codes you provided.

# WordPress on AWS

This project shows how to deploy a WordPress site on AWS using EC2, RDS, and Apache.

## Prerequisites

- An AWS account
- A security group for EC2 with SSH (port 22) and HTTP (port 80) access from anywhere
- A security group for RDS with MySQL/Aurora (port 3306) access from the EC2 security group
- An RDS instance running MySQL or Aurora
- An EC2 instance running Ubuntu 20.04 t2 micro

## Installation

1. SSH into the EC2 instance using your key pair and the public IP address.
2. Update the system packages and install Apache, PHP, and PHP-MySQL modules.


```bash
sudo apt update
sudo apt upgrade
sudo apt install apache2 php php-mysql -y
```

3. Download and unzip the latest WordPress release in the `/tmp` directory.

```bash
cd /tmp
wget https://wordpress.org/latest.zip
sudo apt install unzip
unzip latest.zip
```

4. Move the WordPress files to the Apache web root directory and change the ownership to `www-data`.

```bash
sudo mv wordpress/ /var/www/html
sudo chown -R www-data:www-data /var/www/html/wordpress
```

5. Create a virtual host configuration file for WordPress in the `/etc/apache2/sites-available` directory.

```bash
cd /etc/apache2/sites-available/
sudo nano wordpress.conf
```

6. Paste the following content in the file, replacing `your_domain` with your domain name or public IP address.

```apacheconf
<VirtualHost *:80>
    ServerName your_domain
    DocumentRoot /var/www/html/wordpress

    <Directory /var/www/html/wordpress>
        AllowOverride All
    </Directory>
</VirtualHost>
```

7. Enable the WordPress site and rewrite module, and restart Apache.

```bash
sudo a2ensite wordpress
sudo a2enmod rewrite
sudo systemctl restart apache2
```

8. Visit `http://your_domain/wp-admin/install.php` in your browser and follow the instructions to complete the WordPress installation. You will need to enter the database name, username, password, and endpoint of your RDS instance.

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](^1^) file for details.

¹: https://www.gnu.org/licenses/gpl-3.0.en.html


