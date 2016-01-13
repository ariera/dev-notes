# In native Mac with Homebrew

### How to launch it after installing with **homebrew**
To have launchd start postgresql at login:

    ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents

Then to load postgresql now:

    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist

Or, if you don't want/need launchctl, you can just run:

    postgres -D /usr/local/var/postgres


### to login in mac (with homebrew installation)
1. you need first to create you username's databse `createdb -h localhost`
2. then you can login `psql -h localhost`

### to create a postgres role
`createuser -s -r postgres`

### To restore a dump
`psql -U postgres -w -d database_name -h localhost < ../path/to/dump.sql`
`PGPASSWORD=postgres psql -U postgres -w -d database_name -h localhost < ../path/to/dump.sql`

### A development database.yml looks like this:
    default: &default
      adapter: postgresql
      host: localhost
      encoding: utf8
      reconnect: false
      pool: 5
      username: my_mac_user_name (ie. ariera)
      password:

    development:
      <<: *default
      database: myapp_dev

    test:
      <<: *default
      database: myapp_test


# In vagrant with ubuntu:

### Intall
`sudo apt-get install postgresql libpq-dev`

### Change root password
1. login as root `sudo -u postgres psql`
2. change root password `ALTER USER postgres PASSWORD 'myawesomepassword';`

### To restore a dump
`sudo -u postgres psql database_name < ../path/to/dump.sql`


# How to export from MySQL with compatibility for PostgreSQL

## To dump
```bash
set standard_conforming_strings = 'off';
set backslash_quote = 'on';
mysqldump -u root -pPASSWORD --compatible=postgresql DATABASE_NAME  > dump.sql
```

_(not 100% sure those `set` are necessary. Copied from [wikibooks](https://en.wikibooks.org/wiki/Converting_MySQL_to_PostgreSQL))_


## To import
* Download this script to convert the dump: https://github.com/lanyrd/mysql-postgresql-converter

```bash
set standard_conforming_strings = 'off';
set backslash_quote = 'on';
python db_converter.py dump.sql dump.psql
psql -d DATABASE_NAME -f dump.sql
```

