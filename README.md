# Linux Server Configuration
Readme for FSND Linux-based Server Configuration project

## Site information
The web app is accessible at http://ec2-52-32-234-250.us-west-2.compute.amazonaws.com/

## Server information
- IP: 52.32.234.250
- User: grader
- Password: zKqGyiqiTrz2kN
- SSH port: 2200

Accessible by SSH using RSA key only

## Summary of Configurations
### System and Firewall
- Install Ubuntu updates from apt-get
- Config ufw to only accept incoming connections on 80, 123, 2200
- Config ufw to allow outgoing connections
- Disable password authentication over ssh
- Set PermitRootLogin to 'no'
- Switch SSH port to 2200
- Turn on ufw

### grader user
- Made user grader
- Added Udacity Student key to `~/.ssh/authorized_keys`
- Used `chsh grader -s /bin/bash` to give grader a shell
- Change password with `passwd grader` to `zKqGyiqiTrz2kN`
- Added `/etc/sudoers.d/grader` file specifying grader can `sudo` with password

### Apache server
- Installed apache2 and wsgi
- Installed pip and then flask, sqlalchemy modules
- `git clone https://github.com/jdiii/item-catalog` to /var/www/html/
- move item-catalog from sqlite to postgresql
- Add an app.wsgi file to /var/www/html/item_catalog that imports the item_catalog module
- move session secret such that it is accessible by wsgi
- add OAuth origin and callback URLs to Google Developer Console

### Postgres
- Install postgresql and postgresql-contrib
- Install python-psycopg2 database adapter
- Add user to Postgres called catalog with password `coldsuperiorprice`
- Add user to Linux called catalog with password `nocuous-dogbane-asset`
- Switch item_catalog python files to use postgresql instead of sqlite
- Add line to pg_hba.conf to allow catalog to access only the database catalog, with a password. Only allow access to DB locally.

## Resources Used
Resources used to finish the project:
- http://askubuntu.com/questions/46424/adding-ssh-keys-to-authorized-keys
- http://unix.stackexchange.com/questions/50264/how-to-fix-bash-or-auto-run-bin-bash-on-ssh-login
- https://www.digitalocean.com/community/tutorials/how-to-edit-the-sudoers-file-on-ubuntu-and-centos
- https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04
- http://flask.pocoo.org/docs/0.12/quickstart/
- http://docs.sqlalchemy.org/en/latest/core/engines.html#postgresql
- https://www.digitalocean.com/community/tutorials/how-to-edit-the-sudoers-file-on-ubuntu-and-centos
- http://stackoverflow.com/questions/14564644/postgres-password-authentication-fails
- https://www.postgresql.org/docs/9.3/static/auth-pg-hba-conf.html
- https://discussions.udacity.com/t/how-to-move-a-flask-app-from-using-a-sqlite3-db-to-postgresql/7004/5
