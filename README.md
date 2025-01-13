After cloning the repo,  
Navigate to following paths and make appropiate changes in environment files.

# AngularFrontend

### "CRUD-Full-Stack-App/angular-frontend/src/environments"

open **"environment.prod.ts"** and **"environment.ts"** in text editor and change value for variable **"apiIp"**

apiIp: 'localhost:8080'         &emsp; // testing on localhost or  

apiIp: 'Public-IP'        &emsp; &emsp; &emsp; // Frontend hosted behind Nginx or  

> Note: Not required to mentioned ports if using default 80/443

**If hosting on storage:** Private IP of backend server on same network or Public-IP

apiIp: 'Private-IP:8080'


# Springboot-Backend

### "CRUD-Full-Stack-App/springboot-backend"

Make changes in **".env"** file with following.

DB_URL=jdbc:mysql://serverurl:port/db_name  
DB_USERNAME=username  
DB_PASSWORD=password  

**"CORS_ORIGIN"**  
CORS_ORIGIN=http://localhost:4200         &emsp; // Testing on localhost or   
CORS_ORIGIN=http://Public-IP         &emsp; &emsp; &emsp;  // Frontend hosted behind Nginx

# Nginx configurations

Depending on your configurations open default.conf file from **"/etc/nginx/sites-available/default.conf"** or  
**"/etc/nginx/conf.d/default.conf"** and  
copy default.config file from folder **"CRUD-Full-Stack-App/angular-frontend/nginx/your-configuration-type/"**