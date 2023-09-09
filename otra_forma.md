#instalacion odoo 14
sudo apt update
sudo apt upgrade
cd ~/
sudo wget https://raw.githubusercontent.com/Yenthe666/InstallScript/14.0/odoo_install.sh
sudo chmod +x odoo_install.sh
./odoo_install.sh
nano /etc/odoo-server.conf

#instalar webmin
sudo nano /etc/apt/sources.list

#agregar 
deb http://download.webmin.com/download/repository sarge contrib
#guardar archivo

wget -q -O- http://www.webmin.com/jcameron-key.asc | sudo apt-key add
sudo apt update
sudo apt install webmin
sudo ufw allow 10000

#modulo de pasarela de pago
pip install mercadopago==0.3.4
#instalar modulo mercado

sudo service odoo-server restart && tail -f /var/log/odoo/odoo-server.log

#####instalacion ngix
sudo nano /lib/systemd/system/odoo-server.service

# contenido de odoo-server.service
[Unit]
Description=Odoo

[Service]
Type-simple
PermissionsStartOnly=true
SyslogIdentifier=odoo-server
User=odoo
Group=odoo
ExecStart=/odoo/odoo-server/odoo-bin --config=/etc/odoo-server.conf --addons-path=/odoo/odoo-server/addons/
WorkingDirectory=/odoo/odoo-server/odoo

[Install]
WantedBy=multi-user.target

#guardar archivo

sudo chmod 755 /lib/systemd/system/odoo-server.service
sudo chown root: /lib/systemd/system/odoo-server.service
sudo systemctl start odoo-server

sudo apt-get install nginx
cd /etc/nginx/sites-available/

sudo nano odoo
# contenido de odoo
server {
        server_name artexxxxxx.me;
        server_name www.artexxxxx.me;

        location / {
                proxy_pass       http://127.0.0.1:8069/;
}
}



cd ../sites-enabled/

ln -s /etc/nginx/sites-available/odoo odoo
sudo service nginx reload
sudo service nginx status

#instalando certificado SSL 
sudo apt-get install certbot
sudo apt-get install python3-certbot-nginx
sudo certbot --nginx
sudo certbot renew --dry-run

#instalacion modulos librerias de facturacion
pip install openpyxl
pip install cchardet
pip install pdf417gen
pip3 install xmltodict dicttoxml cchardet cryptography pyOpenSSL pycrypto
pip3 install M2Crypto
pip3 install jsbeautifier
pip3 install woocommerce
pip3 install signxml
sudo apt-get install libssl-dev swig python3-dev gcc
pip3 install SOAPpy
pip3 install suds-py3
pip3 install xlwt
pip3 install zeep