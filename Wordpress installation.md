# Wordpress installation on EC2
## Description : Launch Ubuntu EC2 instance, install wordpress, create mysql database

### Step 1 : **Launch EC2 on ubuntu**
![Screenshot from 2022-01-05 11-23-40](https://user-images.githubusercontent.com/97081058/148174961-7eb8ee16-7d12-403a-9b79-8109dacd1dfc.png)
- Give permission to the .pem file & Connect to the Terminal
```
sudo chmod 400 <YOUR-FILE NAME>
ssh ubuntu@<YOUR IP> -i <YOUR pem.file NAME>
```

![Screenshot from 2022-01-05 11-27-28](https://user-images.githubusercontent.com/97081058/148176037-57907bea-9859-44c4-9bc5-516f793002fe.png)

- Update & Upgrade
```
sudo apt update -y
sudo apt upgrade -y
```
![Screenshot from 2022-01-05 11-30-59](https://user-images.githubusercontent.com/97081058/148176360-76982191-b53f-4df2-9657-dab6f2446bb3.png)
![Screenshot from 2022-01-05 11-31-21](https://user-images.githubusercontent.com/97081058/148176375-0138f415-646a-4722-b542-c5a25080c283.png)

- Install apache server,Start & Enable
```
sudo apt install apache2
sudo systemctl start apache2
sudo systemctl enable apache2
```
![Screenshot from 2022-01-05 11-40-04](https://user-images.githubusercontent.com/97081058/148177162-79aa9374-4beb-4aeb-91a6-77ee5bf38cad.png)
![Screenshot from 2022-01-05 11-41-45](https://user-images.githubusercontent.com/97081058/148177170-cd4aa827-a0fa-495f-b9c0-eb087529f43d.png)

- Install mariadb & Start
```
sudo apt install mariadb-server mariadb-client
sudo systemctl start mariadb
```
- For secure we have to do this things
- Give Ender and give all nessasary permissions (Y/N)
- Restart the mariadb
```
sudo mysql_secure_installation
```
![Screenshot from 2022-01-05 11-44-06](https://user-images.githubusercontent.com/97081058/148177925-6604267b-c845-4afa-b008-76a8502f71e8.png)
![Screenshot from 2022-01-05 11-45-11](https://user-images.githubusercontent.com/97081058/148177934-b9dcf056-f8a1-47f5-9c28-0ce2da1442a2.png)
- Install php
```
sudo apt install php php-mysql php-gd php-cli php-common php-mbstring php-curl php-xml
php-xmlrpc php-soap php-intl php-zip
```
![Screenshot from 2022-01-05 11-48-03](https://user-images.githubusercontent.com/97081058/148178752-4fdb2454-8cfc-4709-a62e-3cca2e0776e4.png)

- [Download Wordpress](https://wordpress.org/download/)
![Screenshot from 2022-01-05 11-49-24](https://user-images.githubusercontent.com/97081058/148179192-1ff637f2-f689-4180-b6a0-d44327cc6266.png)
- For wordpress installation we have to download this two things
```
sudo apt install wget unzip -y
sudo wget <paste the wordpress link>
sudo unzip lastest.zip
```
![Screenshot from 2022-01-05 11-49-58](https://user-images.githubusercontent.com/97081058/148180045-5ea3b1b0-c05f-4f75-a1a8-a0829cf14580.png)
![Screenshot from 2022-01-05 11-50-22](https://user-images.githubusercontent.com/97081058/148180070-e3afec32-3946-4182-aabf-d8af9f6c90b4.png)
![Screenshot from 2022-01-05 11-50-43](https://user-images.githubusercontent.com/97081058/148180091-bcfa91d2-d322-48aa-803a-7767f42ced4b.png)
-We have to copy all the files which is inside the wordpress
-Then copy to the */var/www/html/*
```
sudo cp -r wordpress/* /var/www/html/
```
![Screenshot from 2022-01-05 11-52-26](https://user-images.githubusercontent.com/97081058/148180938-aecdef19-fc62-4349-9606-e1d08a89942b.png)
- Change name root to *www-data:www-data*
```
sudo chown www-data:www-data -R /var/www/html/
ls -l
```
![Screenshot from 2022-01-05 11-53-56](https://user-images.githubusercontent.com/97081058/148181336-7e925cdc-8a0b-470a-a55e-2f9fe7761b68.png)
## After that copy your public IP and paste to the browser URL
### You can see the Apache2 ubuntu Default page
![Screenshot from 2022-01-05 11-54-32](https://user-images.githubusercontent.com/97081058/148181438-f33f03a5-2b87-4346-9575-1c2dfd6b18ee.png)
- Remove or copy somewhere the *index.html*
- And create mysql user and passowrd
```
sudo rm -rf index.html
sudo mysql -u root -p
```
![Screenshot from 2022-01-05 11-55-37](https://user-images.githubusercontent.com/97081058/148181868-f5a89117-96d2-404c-a755-1ff82aadd59c.png)
- (In database creation create the database), create user and password and grant privileges
```
create database <your database name>;
create user "<username>"@"%" identified by "<Password>";
grant all privileges on <databade name>.* to "<username>"@"%";
```
## After created database Refresh your public IP URL
### You can see the following pages
- Select appropriate language
![Screenshot from 2022-01-05 12-02-10](https://user-images.githubusercontent.com/97081058/148183438-573e5004-d62f-4919-80bc-35a03ea03fe0.png)
- Give Let's go
![Screenshot from 2022-01-05 12-02-15](https://user-images.githubusercontent.com/97081058/148183623-43798cd7-82a1-44c2-beb8-4e64c6a9d581.png)
- Now Give the database name,User name,and password then Submit
![Screenshot from 2022-01-05 12-02-30](https://user-images.githubusercontent.com/97081058/148184046-5ab1e880-dd6a-4c68-a0cc-e96eb31a216c.png)
 >Run the Installation
![Screenshot from 2022-01-05 12-02-57](https://user-images.githubusercontent.com/97081058/148184196-e9eb2b9b-a55d-49b9-9a24-32bbaeb988ed.png)
-Give the site name, user name, password & email then give install wordpress
![Screenshot from 2022-01-05 12-03-34](https://user-images.githubusercontent.com/97081058/148184437-f795294b-1a1e-4fd4-8ff4-cac2cc958a26.png)
`login`
![Screenshot from 2022-01-05 12-04-25](https://user-images.githubusercontent.com/97081058/148184860-b7f6924a-e2cb-4563-8296-726332d23ee9.png)
- Enter User name and Password And click Login
![Screenshot from 2022-01-05 12-04-37](https://user-images.githubusercontent.com/97081058/148184982-4d374781-a363-41c1-a622-71b9a85662db.png)
# You can see the wordpress dashboard
![Screenshot from 2022-01-05 12-05-01](https://user-images.githubusercontent.com/97081058/148185207-055f6403-8c6c-47da-bf69-90b37a0d6175.png)

![Screenshot from 2022-01-05 12-05-06](https://user-images.githubusercontent.com/97081058/148185222-3a1e5634-6e2c-4536-a397-0ca25bc7be55.png)
# Documented BY
- ## Parthiban
