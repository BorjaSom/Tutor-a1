# Tutoría 1

## Create LXC container
- `$ sudo lxc-create -t download -n aeodootutoria1 -- --dist ubuntu --release jammy --arch amd64`
- `$ sudo lxc-start -n aeodootutoria1` 
- `$ sudo lxc-attach cursoaeodoo`

### Install Odoo
#### Create User System
- `$ adduser odoo`
#### Install Postgres
- `$ sudo apt-get install postgresql postgresql-client`
- `$ sudo su postgres`
- `$ createuser --createdb --pwprompt odoo`
- ctrl + D
#### DD Odoo Source
- `$ sudo apt-get install git`
- `$ su - odoo`
- `$ git clone https://github.com/Odoo/odoo.git --depth 1 --branch 17.0 --single-branch odoo`
#### Install dependencies
- `$ sudo apt install python3-pip libldap2-dev libpq-dev libsasl2-dev`
- `$ pip install -r /home/odoo/odoo/requirements.txt`
#### Install wkhtml2pdf
- `$ sudo apt-get install -y software-properties-common`
- `$ sudo apt-add-repository -y "deb http://security.ubuntu.com/ubuntu focal-security main"`
- `$ sudo apt-get -yq update`
- `$ sudo apt-get install wget`
- `$ wget "https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.focal_amd64.deb"`
- `$ sudo apt install ./wkhtmltox_0.12.5-1.focal_amd64.deb`
#### Odoo Config
- `$ su odoo`
- `vim /home/odoo/odoo.conf`
	- `[options]
; This is the password that allows database operations:
; admin_passwd = admin
db_host = False
db_port = False
db_user = odoo
db_password = odoo
;addons_path = /usr/lib/python3/dist-packages/odoo/addons
;default_productivity_apps = True`
- check the ip of the container in your system : `$ sudo lxc-info [container name] `
- execute Odoo in the browser [container ip]:8069 
