To set up Nginx to protect a directory using Basic HTTP Auth (also known as Basic HTTP Authentication), you can follow these steps. This example will create a simple configuration to protect a directory with a username and password.

## Requirements
- docker
- docker compose 

## Step 1: Install htpasswd Utility.
If you haven't already, install htpasswd utility, which is part of the Apache HTTP Server tools package.
```bash
sudo apt-get update
sudo apt-get install apache2-utils
```

## Step 2: Create the Password File
Use the htpasswd utility to create a password file. We'll store this file in the nginx/conf.d directory.

```bash
htpasswd -c nginx/conf.d/.htpasswd yourusername
```
* Replace yourusername with the desired username.
* You'll be prompted to enter and confirm the password.

## Step 3: Add Some HTML Content (Optional)
You can create an HTML file to html directory:
```bash
echo "<h1>Welcome to the Nginx server!</h1>" > html/index.html
```

## Step 4: Start the Docker Compose Setup
Run the following command from the root directory:
```bash
sudo docker compose up -d
```

This will start the Nginx server with the Basic Authentication enabled for the /protected-dir/ path.

## Step 5: Access the Protected Directory
Open your browser and navigate to http://localhost:8080/protected-dir/. You should be prompted to enter the username and password you configured earlier.
