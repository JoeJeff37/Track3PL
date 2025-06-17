# STEPS IN ACHIEVING THE PROJECT

##  Server Setup 

1. **Created an AWS EC2 Instance**  
   - Used Ubuntu 
   - Allowed ports:  
     - **22** (SSH)  
     - **80** (HTTP)  
     - **443** (HTTPS)

2. **Connected to my Server**
   ```
   ssh -i "irl-key.pem" ubuntu@ec2-3-252-124-53.eu-west-1.compute.amazonaws.com
   ```

---

##  Updated & Installed Dependencies

1. **Updated Packages**
   ```
   sudo apt update && sudo apt upgrade -y
   ```

2. **Installed Node.js & npm**
   ```
   sudo apt install nodejs npm -y
   ```

   ```

3. **Installed Git**
   ```
   sudo apt install git -y
   ```

---

## Setup my Node.js App

1. **Installed dependencies**
   ```
   npm install
   ```
2. **Created my App's file structure**

    ```
     mkdiir Track3PL
    nano index.html
    cd Track3PL
    nano index.html

    ```
3. **Tested my app**
   ```
   node server.js
   ```

---

## Ran my App with a Process Manager

1. **Installed PM2**
   ```
   sudo npm install -g pm2
   ```

2. **Started my app**
   ```
   pm2 start app.js
   ```

3. **Enabled PM2 Startup Script**
   ```
   pm2 startup
   pm2 save
   ```

---

## Installed & Configured NGINX

1. **Installed NGINX**
   ```
   sudo apt install nginx -y
   ```

2. **Started & Enabled NGINX**
   ```
   sudo systemctl start nginx
   sudo systemctl enable nginx
   ```

3. **Configured a Reverse Proxy**
   ```
   sudo nano /etc/nginx/sites-available/Track3PL.mooo.com
   ```

   ```nginx
   server {
       listen 80;
       server_name Track3PL.mooo.com www.Track3PL.mooo.com;

       location / {
           proxy_pass http://localhost:3000;
           proxy_http_version 1.1;
           proxy_set_header Upgrade $http_upgrade;
           proxy_set_header Connection 'upgrade';
           proxy_set_header Host $host;
           proxy_cache_bypass $http_upgrade;
       }
   }
   ```

4. **Enabled the Config**
   ```
   sudo ln -s /etc/nginx/sites-available/Track3PL.mooo.com /etc/nginx/sites-enabled/
   ```

5. **Tested the NGINX Config**
   ```
   sudo nginx -t
   ```

6. **Restarted NGINX**
   ```
   sudo systemctl restart nginx
   ```

---

## Secure with HTTPS (Let’s Encrypt)

1. **Installed Certbot**
   ```
   sudo apt install certbot python3-certbot-nginx -y
   ```

2. **Obtained & Installed SSL**
   ```
   sudo certbot --nginx 
   ```

3. **Entered my email at the prompt**
    
4. **Entered Yes twice for confirmation**

## Deployment to Github
1. **Created and added SSH Key**
2. **Linked the SSH Key**
3. **Initialized Git and pushed to Github**

### Public ip address 3.252.124.53

![Landing Page Screenshot](/img/"landing-page-website.png")
