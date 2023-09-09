# infotrixs
WordPress site over AWS using RDS


# WordPress on AWS

![AWS Logo](https://your-image-link.com/aws-logo.png)

This project demonstrates how to deploy a WordPress site on AWS using EC2, RDS, and Apache.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Prerequisites

Before you begin, ensure you have met the following requirements:

- An AWS account with appropriate permissions.
- A security group for EC2 with SSH (port 22) and HTTP (port 80) access from anywhere.
- A security group for RDS with MySQL/Aurora (port 3306) access from the EC2 security group.
- An RDS instance running MySQL or Aurora.
- An EC2 instance running Ubuntu 20.04 instance type t2-micro.

## Installation

To deploy WordPress on AWS, follow these steps:

1. SSH into the EC2 instance using your key pair and the public IP address.
   ```bash
   ssh -i your-key.pem ec2-user@your-ec2-ip
   ```

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

## Usage

Provide instructions and examples for users to use your project once it's deployed.

## Contributing

To contribute to this project, follow these steps:

1. Fork this repository.
2. Create a branch: `git checkout -b feature/your-feature-name`.
3. Make your changes and commit them: `git commit -m 'Add some feature'`.
4. Push to the original branch: `git push origin feature/your-feature-name`.
5. Create a pull request.

## License

This project is licensed under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for details.

---






