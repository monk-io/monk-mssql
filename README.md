# MSSQL & Monk
This repository contains Monk.io template to deploy MSSQL either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

# Prerequisites
- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

#### Make sure monkd is running.
```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository
```bash
git clone https://github.com/monk-io/monk-mssql
```

## Load Template
```bash
cd monk-mssql
monk load MANIFEST
```


#### Let's take a look at the themes I have installed.
```bash
foo@bar:~$ monk list monk-mssql
✔ Got the list
Type      Template          Repository  Version  Tags
runnable  monk-mssql/mssql  local       -        -
group     monk-mssql/stack  local       -        -
```

## Deploy Stack
```bash
foo@bar:~$ monk run monk-mssql/stack
✔ Starting the job: local/monk-mssql/stack... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% mcr.microsoft.com/mssql/server:latest mnk-1
✔ Checking/pulling images DONE
✔ Started local/monk-mssql/stack

🔩 templates/local/monk-mssql/stack
 └─🧊 Peer mnk-1
    └─🔩 templates/local/monk-mssql/mssql
       └─📦 c4e9a1d5c9bbbace517f4ecfa751369d-al-monk-mssql-mssql-monk-mssql
          ├─🧩 mcr.microsoft.com/mssql/server:latest
          ├─💾 /var/lib/monkd/volumes/monk-hadoop -> /var/opt/mssql
          └─🔌 open 13.50.109.100:1433 (0.0.0.0:1433) -> 1433

💡 You can inspect and manage your above stack with these commands:
	monk logs (-f) local/monk-mssql/stack - Inspect logs
	monk shell     local/monk-mssql/stack - Connect to the container's shell
	monk do        local/monk-mssql/stack/action_name - Run defined action (if exists)
💡 Check monk help for more!
```

## Variables
The variables are in `stack.yml` file. You can quickly setup by editing the values here.

| Variable                     	| Description                               	|
|------------------------------	|-------------------------------------------	|
| mssql_port                    | MSSQL database port, Default: 1433 	               |
| mssql_password                | MSSQL SA database password, Default P@ssw0rd                     	|


## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```

