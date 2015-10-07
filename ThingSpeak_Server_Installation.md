* Change "pi" account password:

passwd

* Set ROOT password, so you can then use root (just for very, very special things!)

sudo passwd root

* System Update & upgrade  :

sudo apt-get update            
sudo apt-get upgrade          
sudo apt-get dist-upgrade   
sudo sync
sudo reboot

* Install additional packages

sudo apt-get -y install build-essential git mysql-server mysql-client libmysqlclient-dev libxml2-dev libxslt-dev libssl-dev libsqlite3-dev

* Configure MySQL

mysql --user=root mysql --password=x9osnmsm
* when in MySQL
mysql> CREATE USER 'thing'@'localhost' IDENTIFIED BY 'speak’;
mysql> GRANT ALL ON *.* TO 'thing'@'localhost' WITH GRANT OPTION;
mysql> commit;
mysql> exit;

* Ruby & Rails install

wget http://cache.ruby-lang.org/pub/ruby/2.1/ruby-2.1.5.tar.gz
tar xvzf ruby-2.1.5.tar.gz
cd ruby-2.1.5
./configure
make
sudo make install
cd ..
echo "gem: --no-rdoc --no-ri" >> ${HOME}/.gemrc
sudo gem install rails

* ThingSpeak Server Install

git clone https://github.com/iobridge/thingspeak.git
cp thingspeak/config/database.yml.example thingspeak/config/database.yml
cd thingspeak
bundle install
bundle exec rake db:create

* verify thingspeak server database installation
mysql --user=root mysql -p
mysql> show databases;
mysql> exit; 

* IF all OK continue with loading Thingspeak DB configuration

bundle exec rake db:schema:load

* RUN the THINGSPEAK SERVER:

pi@RPIMON1 ~/thingspeak $ rails server webrick
