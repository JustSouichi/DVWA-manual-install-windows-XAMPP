# **Manually Install and Run DVWA on Windows using XAMPP**

## **1. Install XAMPP**
1. Download **XAMPP** from [apachefriends.org](https://www.apachefriends.org/download.html).
2. Install **XAMPP** and select the following components:
   - Apache
   - MySQL
   - PHP
3. Open **XAMPP Control Panel** and **Start** both:
   - Apache
   - MySQL

---

## **2. Download and Move DVWA to XAMPP**
1. Download **DVWA** from GitHub:
   - [GitHub DVWA](https://github.com/digininja/DVWA)
   - Click **Code → Download ZIP** and extract it.
2. Move the extracted **DVWA** folder to:
   ```
   C:\xampp\htdocs\dvwa
   ```

---

## **3. Configure MySQL Database**
1. Open **XAMPP Control Panel** → Click **Admin** next to MySQL.
2. phpMyAdmin will open in a browser.
3. Click on the **SQL** tab and execute the following commands:
   ```sql
   CREATE DATABASE dvwa;
   CREATE USER 'dvwauser'@'localhost' IDENTIFIED BY 'dvwa123';
   GRANT ALL PRIVILEGES ON dvwa.* TO 'dvwauser'@'localhost';
   FLUSH PRIVILEGES;
   ```
4. Click **Go** to execute.

---

## **4. Configure DVWA**
1. Navigate to:
   ```
   C:\xampp\htdocs\dvwa\config\
   ```
2. Rename `config.inc.php.dist` to `config.inc.php`.
3. Open `config.inc.php` with **Notepad** or any text editor.
4. Update the database credentials:
   ```php
   $_DVWA[ 'db_server' ]   = '127.0.0.1';
   $_DVWA[ 'db_database' ] = 'dvwa';
   $_DVWA[ 'db_user' ]     = 'dvwauser';
   $_DVWA[ 'db_password' ] = 'dvwa123';
   ```
5. Save and close the file.

---

## **5. Configure PHP and Enable Required Extensions**
1. Open:
   ```
   C:\xampp\php\php.ini
   ```
2. Search (`CTRL + F`) for the following lines and **uncomment (remove `;`)**:
   ```ini
   extension=mysqli
   extension=gd
   allow_url_include = On
   ```
3. Save the file and restart **Apache** in XAMPP.

---

## **6. Run DVWA**
1. Open your browser and go to:
   ```
   http://localhost/dvwa/setup.php
   ```
2. Click on **"Create / Reset Database"**.
3. Log in using:
   ```
   Username: admin
   Password: password
   ```

---

## **7. Adjust DVWA Security Settings (Optional)**
1. Go to **DVWA Security** settings.
2. Set Security Level to **low** to practice vulnerabilities.

---

## **Troubleshooting**
- If you get a **MySQL connection error**, try using:
  ```php
  $_DVWA[ 'db_server' ]   = 'localhost';
  ```
- If `allow_url_include` is off, manually change it in `php.ini`.
- If Apache doesn't start, make sure **Skype, IIS, or any other service** is not using port 80.

---

Now, DVWA is fully set up and running on Windows with XAMPP! 🚀
