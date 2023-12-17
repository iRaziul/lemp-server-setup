# LEMP Stack Website Setup: Step-by-Step Guide for Hosting Your Website with Nginx

Setting up a website typically involves configuring a web server, creating a website directory, setting up a domain or subdomain, and placing website files within the directory.
If you're using a LEMP stack and want to set up a website, here's a basic guide:

**1. Configure Nginx:**

Create an Nginx server block for your website. For instance, if your domain is `example.com` or your subdomain is `subdomain.example.com`:

```bash
sudo nano /etc/nginx/sites-available/example.com
```

**2. Add Nginx Configuration:**

Configure the server block by specifying the root directory for your website and other settings:

```nginx
server {
    listen 80;
    server_name example.com www.example.com; # Replace with your domain

    root /var/www/example.com; # Replace with your website's directory path
    index index.html index.htm index.php; # Adjust based on your site's file structure

    location / {
        try_files $uri $uri/ =404;
    }
}
```

**3. Create Website Directory:**

Create the directory for your website files:

```bash
sudo mkdir -p /var/www/example.com
```

**4. Enable the Nginx Server Block:**

Create a symbolic link to enable the server block and reload Nginx:

```bash
sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```

**5. Place Website Files:**

Upload or create your website files within the `/var/www/example.com` directory. Ensure your index file (e.g., `index.html`, `index.php`) is present.

**6. Domain Configuration:**

If using a domain, configure your domain registrar's DNS settings to point to your server's IP address.

**7. Testing:**

Visit your domain/subdomain in a web browser (`http://example.com` or `http://subdomain.example.com`) to verify that your website is accessible.

This basic setup assumes static content or a PHP-based website. Adjust the Nginx configuration and website files according to your specific requirements, such as supporting PHP or other scripting languages, handling SSL/TLS, or configuring additional server directives.
