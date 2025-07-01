# Erpnext-15
Erpnext 15 complete setup guide

#update sudo...
sudo apt-get update -y
sudo apt-get upgrade -y

#create user
sudo adduser [frappe user]
usermod -aG sudo [frappe user]
su [frappe user]
cd /home/[frappe user]

#install required dependencies
sudo apt-get install git   ---> install git
sudo apt-get install -y xvfb libfontconfig1 wkhtmltopdf ---> font, customization, html, and pdf reader library
sudo apt-get install -y libmysqlclient-dev  ---> C headers/libs to build software with MySQL

sudo apt-get install python3.10-venv ---> python install
sudo apt-get install software-properties-common ---> tool to manage software sources
sudo apt install mariadb-server mariadb-client --->  install mariadb server /  command-line client to connect mariadb Server
sudo apt-get install redis-server  ---> Install Redis Server

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash  --->  Install NVM
source ~/.bashrc ---> load nvm to current terminal
command -v nvm ---> verify nvm
nvm install 18 ---> install node.js 18

nvm use 18 ---> set node.js as default
nvm alias default 18

sudo apt-get install npm ---> install npm
sudo apt-get install -g yarn  ---> install yarn

sudo pip3 install frappe-bench ---> install frappe
bench init --frappe-branch version-15 frappe-bench ---> connect with frappe branch 

sudo chmod -R o+rx /home/[frappe user] ---> authorize frappe user
bench new-site [site name] ---> create new site
bench use [site name]  ---> use default site

bench get-app payments ---> get payments app 
bench get-app --branch version-15 erpnext ---> get erpnext app
bench get-app hrms ---> get hrms app

bench --site [site name] install-app erpnext ---> install erpnext app
bench --site [site name ] install-app hrms ---> install hrms app

bench start  ---> start server 
