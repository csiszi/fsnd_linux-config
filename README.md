# Udacity Linux Server Configuration

## How to access
- IP: 52.34.145.16
- SSH Port: 2200
- Web: http://ec2-52-34-145-16.us-west-2.compute.amazonaws.com/

## Steps
- generated locale (`locale-gen hu_HU.UTF-8`)
- added user grader and catalog w/ sudo access
- expired grader's password (`chage -d 0 grader`)
- installed provided key for grader and my own for catalog
- updated `/etc/hostname` and `/etc/hosts` to get rid of the error messages after sudo
- updated packages (`apt-get update`)
- upgraded packages (`apt-get upgrade`)
- changed ssh port in `/etc/ssh/sshd_config`
- restarted SSH (`service ssh restart`)
- configured/enabled ufw
- updated timezone (`dpkg-reconfigure tzdata`)
- installed the following linux apps:
  - apache2
  - libapache2-mod-wsgi
  - postgresql
  - git
  - python-pip
  - python-psycopg2
- installed via pip:
  - SQLAlchemy
  - oauth2client
  - requests
  - httplib2
  - flask
- installed item catalog project to `/var/www/catalog`
- configured apache to load `/var/www/catalog/catalog.wsgi`
- changed the app to use postgresql (instead of sqlite)
- updated the app's clients_secrets.json files
- figured out that I have to set app.secret_key in the wsgi file
- added user catalog to postgresql, checked that only local connections allowed
- addedd .htaccess disallow .git access

## Resources used
https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
http://askubuntu.com/questions/323131/setting-timezone-from-terminal
http://www.cyberciti.biz/faq/howto-add-postgresql-user-account/
http://stackoverflow.com/questions/6142437/make-git-directory-web-inaccessible
