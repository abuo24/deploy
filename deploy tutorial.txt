ssh root@157.230.108.63 (with login)
cd ~/.ssh

// local machine generate key
ssh-keygen

nano authorized_keys (put local machine ssh public key)

///java install
sudo add-apt-repository ppa:linuxuprising/java
sudo apt-get update
sudo apt-get install oracle-java16-installer


//////postgres from officail site
# Create the file repository configuration:
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

# Import the repository signing key:
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

# Update the package lists:
sudo apt-get update

# Install the latest version of PostgreSQL.
# If you want a specific version, use 'postgresql-12' or similar instead of 'postgresql':
sudo apt-get -y install postgresql


//////postgres hba location

cd /etc/postgresql/13/main

////change hba file

sudo service postgresql restart




sudo -i -u postgres
psql

///////create db, user, role

CREATE DATABASE mobitech;
CREATE USER mobitech WITH ENCRYPTED PASSWORD 'mobitech';
GRANT ALL PRIVILEGES ON DATABASE mobitech TO mobitech;


////process management  ////pid
lsof -i tcp:9000
kill -9 pid
killall java

nohup java -jar -Dspring.profiles.active=prod *.jar &

nohup java -jar mod.jar &

mvn clean install package -Dmaven.test.skip=true
