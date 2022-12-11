--check port usage

sudo lsof -i -P -n | grep LISTEN
sudo netstat -tulpn | grep LISTEN
sudo ss -tulpn | grep LISTEN
sudo lsof -i:22 ## see a specific port such as 22 ##
sudo nmap -sTU -O IP-address-Here

install java and git first

wget https://www.atlassian.com/software/stash/downloads/binary/atlassian-bitbucket-7.21.7-x64.bin
chmod +x atlassian-bitbucket-7.21.7-x64.bin

https://installvirtual.com/install-postgresql-10-on-amazon-ec2/
sudo amazon-linux-extras install postgresql10
amazon-linux-extras install postgresql10 vim epel -y
yum install -y postgresql-server postgresql-devel
/usr/bin/postgresql-setup --initdb
systemctl enable postgresql
su - postgres
psql

CREATE SCHEMA bitbucketdb;
CREATE USER bitbucket PASSWORD 'asd@123';
GRANT ALL ON SCHEMA bitbucketdb to bitbucket;
GRANT ALL ON ALL TABLES IN SCHEMA bitbucketdb to bitbucket;
--CREATE ROLE bitbucketuser WITH LOGIN PASSWORD 'asd@123' VALID UNTIL 'infinity';
CREATE DATABASE bitbucketdb WITH ENCODING='UTF8' OWNER=bitbucket CONNECTION LIMIT=-1;

change pg_hba.conf to md5#ident under data folder
systemctl restart postgresql

cd /opt/
./atlassian-Bitbucket-X.X.X-x64.bin

psql --version