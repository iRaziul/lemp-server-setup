# MySQL Database Creation Instructions

This guide provides step-by-step instructions for creating a MySQL database and associating a user with it using the command-line interface.

## Prerequisites

Ensure you have access to a MySQL server and the necessary privileges to create databases and users.

## Steps to Create a Database and User

1. **Log in to MySQL:**

   ```bash
   mysql -u root -p
   ```

2. **Create the Database:**

   ```sql
   CREATE DATABASE digimax;
   ```

3. **Create a User for the Database:**

   ```sql
   CREATE USER 'digimax_user'@'localhost' IDENTIFIED BY 'password';
   ```

4. **Grant Privileges to the User:**

   ```sql
   GRANT ALL PRIVILEGES ON digimax.* TO 'digimax_user'@'localhost';
   ```

5. **Apply Changes and Exit:**
   ```sql
   FLUSH PRIVILEGES;
   EXIT;
   ```

Make sure to replace `digimax`, `digimax_user`, and `password` with your desired database name, username, and secure password.

These steps enable you to create a MySQL database named "digimax" and associate the user "digimax_user" with full privileges on that database.

_For more details and customization options, refer to [MySQL Documentation](https://dev.mysql.com/doc/)._

Feel free to modify these instructions based on your specific requirements and preferences.
