# InstallOdoo
Command with comments to install Odoo 11

## CREATE DEV USER ##

useradd -m -g sudo -s /bin/bash vinodoo  # Create an 'odoo' user with sudo powers
passwd vinodoo  # Ask and set a password for the new user

## LOGIN AS DEV USER  AND PREPARE ENVIRONMENT ##

sudo apt-get update && sudo apt-get upgrade  #Install system updates
sudo apt-get install git  # Install Git
sudo apt-get install npm  # Install NodeJs and its package manager
sudo ln -s /usr/bin/nodejs /usr/bin/node  # call node runs nodejs
sudo npm install -g less less-plugin-clean-css  #Install less compiler
mkdir ~/odoo-dev  # Create a directory to work in
$ cd ~/odoo-dev  # Go into our work directory
$ git clone https://github.com/odoo/odoo.git -b 11.0 --depth=1  # Get Odoo source code

sudo apt-get install build-essential libssl-dev libffi-dev python3-dev
sudo apt-get install libsasl2-dev libldap2-dev libssl-dev python3-pip
cd odoo
pip3 install -r requirements.txt
sudo su - postgres -c "createuser -s $USER" ## create postgreSQL user same as current log in user with super user priviledge

## START THE ODOO SERVER ##
	


./odoo-bin

