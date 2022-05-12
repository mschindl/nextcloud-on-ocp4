DEPLOYMENT STEPS for NextCloud on OpenShift 4.x (4.9) with OpenShift Data Foundation
 
1. Create the Persistent Volume Claim for both Apache files and Database using the file: nextcloud-shared-pvc.yaml
oc create -f nextcloud-shared-pvc.yaml

2. Create a secret called nextcloud-db-secret for the db with the variables and content: MYSQL_ROOT_PASSWORD MYSQL_USER MYSQL_PASSWORD

oc create -f secret-db.yaml

secret-db.yaml > Notes:
      mysql-root-password:  # Test1234
      mysql-user:  # testadm
      mysql-password: # Test1234

3. Create the Mariadb Pod using the file: nextcloud-db.yaml
oc create -f nextcloud-db.yaml

4. Create the Webserver Pod using the file: nextcloud-server.yaml
oc create -f nextcloud-server.yaml

5. After that, create the routes/ingresses to the webserver on port: 80
8443 should be used instead of 80
 
6. Last step is access the address where Nextcloud is running (defined in the ingress/route) and configure the admin user and password as
much as mySQL as Database with the information stored on the secret with the variables above (MYSQL_ROOT_PASSWORD, MYSQL_USER and MYSQL_PASSWORD)
after that you should be able to start using the environment.
 
