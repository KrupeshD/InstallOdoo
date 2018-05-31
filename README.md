# Setup Odoo 11 Dev enviornment on Ubuntu 16.04 LTS #


#### Run the following commands to install the main dependencies:

```
sudo apt-get update && sudo apt-get upgrade 
sudo apt-get install -y git python3.5 postgresql nano virtualenv \
						xz-utils wget fontconfig libfreetype6 \ 
						libx11-6 libxext6 libxrender1 \
						node-less node-clean-css xfonts-75dpi
 ```
						


#### Download and install wkhtmltopdf tool - runtime dependency of Odoo used to produce PDF reports.

```
wget -O wkhtmltox.tar.xz https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz 
tar xvf wkhtmltox.tar.xz
sudo mv wkhtmltox/lib/* /usr/local/lib/
sudo mv wkhtmltox/bin/* /usr/local/bin/
sudo mv wkhtmltox/share/man/man1 /usr/local/share/man/
```

#### Install the build dependencies

```
sudo apt-get install -y gcc python3.5-dev libxml2-dev \
						libxslt1-dev libevent-dev libsasl2-dev libssl-dev libldap2-dev \
						libpq-dev libpng-dev libjpeg-dev
```

#### Configure PostgreSQL

```
sudo -u postgres createuser --createdb $(whoami)
createdb $(whoami)
```

#### Configure Git - Optional

```
git config --global user.name  <<Your Name>>
git config --global user.email <<youremail@example.com>>
```

#### Clone the Odoo code from Github:

-- Here, you can either choose the official Odoo branch or the Odoo Community Association (OCA) branch.
-- If you want to clone the community association branch then clone following repo.
-- Fixes and improvements are peer-reviewed by the community and tend to be merged faster in the OCA brach than on the official branch.

```
mkdir ~/odoo-dev
cd ~/odoo-dev
```
==> Official Brach
```
git clone https://github.com/odoo/odoo.git -b 11.0 --depth=1 
```
==> OCA brach.
```
git clone https://github.com/OCA/OCB.git odoo -b 11.0 --depth=1 -- OCA brach.
```

-- Once the repository is cloned, change directory to odoo.

```
cd odoo
```

#### Create an python virtual environment and activate it.

```
virtualenv -p python3 ~/odoo-11.0
source ~/odoo-11.0/bin/activate
```

#### Install dependencies of Odoo in the virtualenv

```
pip3 install -r requirements.txt
```

#### Create and start your first Odoo instances:

```
createdb odoo-test
python3 odoo-bin -d odoo-test --addons-path=addons --db-filter=odoo-test$
```

##### Point your browser to http://localhost:8069 and authenticate it using the admin account and admin as password.

## For more secured envornment ##

#### ignore createdb command and start odoo server using the following command. 

```
python3 odoo-bin
```

#### Now you can set the database name and user login. When you open http://localhost:8069

