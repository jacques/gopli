gopli
========
Database backup between remote hosts (or local) written in Golang.

# Notice
Currently MySQL only.
But it will adapt to other management systems like postgresql etc...

## Install
```
go get github.com/timakin/gopli
```

## Usage
Write down setting file in toml.
```
[database]
  [database.local]
  host = "localhost"
  management_system = "mysql"
  name = "app_development"
  user = "root"
  password = ""

  [database.staging]
  host = "xxx.xxx.xxx.xxx"
  management_system = "mysql"
  name = "app_staging"
  user = "root"
  password = ""

  [database.production]
  host = "yyy.yyy.yyy.yyy"
  management_system = "mysql"
  name = "app_production"
  user = "root"
  password = ""

[ssh]
  [ssh.local]
  host = "localhost" # or "127.0.0.1"

  [ssh.staging]
  host = "xxx.xxx.xxx.xxx"
  port = "22"
  user = "timakin"
  key = "~/.ssh/id_rsa_staging"

  [ssh.production]
  host = "yyy.yyy.yyy.yyy"
  port = "22"
  user = "remoteuser"
  key = "~/.ssh/id_rsa_prod"

```

```
gopli sync -from production -to staging -c config/gopli.toml
```
