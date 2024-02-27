# loadbalancer
Tutorial für die Einrichtung eines NGINX-Webservers auf einer EC2-Instanz mit einem GitHub-Repository 

Git Installation und Repository-Cloning:

bash

sudo yum update -y

sudo yum install git

cd /home/ec2-user/

sudo git clone https://github.com/davlongo/loadbalancer.git

NGINX Installation und Konfiguration:

bash

sudo yum install nginx -y

sudo service nginx start

NGINX-Konfigurationsdatei erstellen:

bash

cd /etc/nginx/conf.d/

sudo nano banana.conf

Hier fügst du deine NGINX-Konfiguration ein:


server {
    listen 80;
    server_name DEINE EC2 IP;

location / {
        root /home/ec2-user/loadbalancer;
        index index.html;
    }
}
Speichere die Datei und schließe den Editor.



NGINX-Status überprüfen:

bash

sudo systemctl status nginx

Berechtigungen für das Verzeichnis setzen:

bash

sudo chmod -R 755 /home/ec2-user
sudo chown -R ec2-user:ec2-user /home/ec2-user

NGINX-Dienst aktivieren und neu starten:

bash

sudo systemctl enable nginx
sudo systemctl restart nginx


Die einzige Sache, die ich hinzugefügt habe, ist die Git-Installation und das Repository-Cloning. Alles andere sieht gut aus. Beachte, dass die IP-Adresse in der NGINX-Konfiguration durch deine spezifische IP-Adresse oder den Domainnamen ersetzt werden sollte, unter dem dein Server erreichbar sein soll.
