# Comandos Ejecutados - Servidor LAMP

## Instalación

### Apache
```bash
sudo apt-get update
sudo apt-get install -y apache2
apache2 -v
```

### MySQL
```bash
sudo apt-get install -y mysql-server
sudo mysql_secure_installation
mysql --version
```

### PHP
```bash
sudo apt-get install -y php libapache2-mod-php php-mysql
php -v
```

## Configuración de MySQL
```bash
sudo systemctl start mysql
sudo systemctl enable mysql

sudo mysql << EOF
CREATE DATABASE tp_final_db;
CREATE USER 'alumno'@'localhost' IDENTIFIED BY 'practica123';
GRANT ALL PRIVILEGES ON tp_final_db.* TO 'alumno'@'localhost';
FLUSH PRIVILEGES;
EOF
```

## Configuración de Apache
```bash
sudo a2enmod rewrite
sudo a2enmod php8.1
sudo systemctl restart apache2
sudo systemctl enable apache2
```

## Creación de Archivos Web
```bash
sudo nano /var/www/html/index.html
sudo nano /var/www/html/info.php
sudo nano /var/www/html/test_db.php
```

## Permisos
```bash
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```

## Verificación
```bash
sudo systemctl status apache2
sudo systemctl status mysql
sudo netstat -tlnp | grep :80
sudo netstat -tlnp | grep :3306
```

## URLs de Acceso

- Página principal: http://[IP_VM]/
- Info PHP: http://[IP_VM]/info.php
- Test DB: http://[IP_VM]/test_db.php

## Notas

- Todo funcionó correctamente al primer intento
- Los tres archivos web responden correctamente
- Conexión a MySQL exitosa
