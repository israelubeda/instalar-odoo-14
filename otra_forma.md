sudo apt update
sudo apt upgrade
cd ~/
sudo wget https://raw.githubusercontent.com/Yenthe666/InstallScript/14.0/odoo_install.sh
sudo chmod +x odoo_install.sh
./odoo_install.sh
nano /etc/odoo-server.conf
sudo nano /etc/apt/sources.list
wget -q -O- http://www.webmin.com/jcameron-key.asc | sudo apt-key add
sudo apt update
sudo apt install webmin
sudo ufw allow 10000
pip install mercadopago==0.3.4
sudo service odoo-server restart && tail -f /var/log/odoo/odoo-server.log
cd /odoo/custom/addons/mercado__pago
ls
nano controllers/controller.py
sudo service odoo-server restart && tail -f /var/log/odoo/odoo-server.log
cd /
cd /odoo/odoo-server/
ls -la
sudo nano /lib/systemd/system/odoo-server.service
ls
cat /etc/odoo.conf
ls /etc
sudo nano /lib/systemd/system/odoo-server.service

sudo chmod 755 /lib/systemd/system/odoo-server.service
sudo chown root: /lib/systemd/system/odoo-server.service
sudo systemctl start odoo-server

sudo apt-get install nginx
cd /etc/nginx/

cd sites-available/
sudo nano odoo
cd ../sites-enabled/

ln -s /etc/nginx/sites-available/odoo odoo
sudo service nginx reload
sudo service nginx status
sudo apt-get install certbot
sudo apt-get install python3-certbot-nginx
sudo certbot --nginx
sudo certbot renew --dry-run
