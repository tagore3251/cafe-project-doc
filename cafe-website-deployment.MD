# Installing Apache (httpd), MariaDB, and PHP on Linux

**Step 1: Update the System**

For Amazon Linux / RHEL / CentOS
```
sudo yum update -y 
```
For Ubuntu/Debian
```
sudo apt update -y
```

**Step 2: Install Apache (httpd)**

For Amazon Linux / RHEL / CentOS
```
sudo yum install httpd -y
```
For Ubuntu/Debian
```
sudo apt install apache2 -y
``` 

Start and Enable Apache

For Amazon Linux / RHEL / CentOS
```
sudo systemctl start httpd
```
```
sudo systemctl enable httpd
``` 
For Ubuntu/Debian
```
sudo systemctl start apache2
```
```
sudo systemctl enable apache2  
```

**Step 3: Install MariaDB (MySQL)**

For Amazon Linux / RHEL / CentOS
```
sudo yum install mariadb105-server -y
```
For Ubuntu/Debian
```
sudo apt install mariadb105-server -y
```

Start and Enable MariaDB
```
sudo systemctl start mariadb
```
```
sudo systemctl enable mariadb
```
 
Secure MariaDB Installation
```
sudo mysql_secure_installation
```
• Follow the on-screen instructions to set a root password and secure the database.

**Step 4: Install PHP**

For Amazon Linux / RHEL / CentOS
```
sudo yum install php php-mysqlnd -y
```
For Ubuntu/Debian
```
sudo apt install php libapache2-mod-php php-mysql -y 
```
 
**Step 5: Restart Apache to Apply Changes**

For Amazon Linux / RHEL / CentOS
```
sudo systemctl restart httpd
```
For Ubuntu/Debian
```
sudo systemctl restart apache2 
```

**Step 6:**

This command creates a symbolic link named environment inside /home/
ec2-user/ that points to the /var/www/ directory.

Any changes you make in /home/ec2-user/environment will reflect in /var/www/, and vice versa.
```
ln -s /var/www/ /home/ec2-user/environment
```

**Step 7:**

```
cd /home/ec2-user/environment
```

**Step 8:**

To download the setup file
```
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-200-ACACAD-3-113230/03-lab-mod5-challenge-EC2/s3/setup.zip
```

**Step 9:**

```
unzip setup.zip
```

**Step 10:**

To download the db file
```
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-200-ACACAD-3-113230/03-lab-mod5-challenge-EC2/s3/db.zip
```

**Step 11:**

```
unzip db.zip
```

**Step 12:**

To download the cafe file
```
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-200-ACACAD-3-113230/03-lab-mod5-challenge-EC2/s3/cafe.zip
```

**Step 13:**

```
unzip cafe.zip -d /var/www/html/
```

**Step 14:** 

```
cd /var/www/html/cafe/
```

**Step 15:**

```
wget https://docs.aws.amazon.com/aws-sdk-php/v3/download/aws.zip
```

**Step 16:**

```
wget https://docs.aws.amazon.com/aws-sdk-php/v3/download/aws.phar
```

**Step 17:**

```
unzip aws -d /var/www/html/cafe/
```

**Step 18:**

```
chmod -R +r /var/www/html/cafe/
```

**Step 19:**

```
cd
```
```
cd /home/ec2-user/environment/setup/
```
```
./set-app-parameters.sh
```

**Step 20:**

```
cd ..
```
```
cd db/
```
```
./set-root-password.sh
```
```
./create-db.sh
```

**Step 21:**

set the timezone
```
sudo sed -i "2i date.timezone = \"America/New_York\" " /etc/php.ini
```

**Step 22:**

```
sudo service httpd restart
```