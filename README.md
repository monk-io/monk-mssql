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
git clone https://github.com/monk-io/mssql
```

## Load Template

```bash
cd mssql
monk load MANIFEST
```

#### Let's take a look at the themes I have installed.

```bash
foo@bar:~$ monk list mssql
✔ Got the list
Type      Template          Repository  Version  Tags
runnable  mssql/db  local       -        -
```

## Deploy Stack

```bash
? Select which 'mssql/db' to run local/mssql/db
✔ Starting the run job: local/mssql/db... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images DONE
✔ Starting containers DONE
✔ New container local-0b18968c2d1d7edc16396ba4d8-local-mssql-db-mssql created DONE
✔ Started local/mssql/db
🔩 templates/local/mssql/db
 └─🧊 Peer local
    └─🔩 templates/local/mssql/db
       └─📦 local-0b18968c2d1d7edc16396ba4d8-local-mssql-db-mssql running
          ├─🧩 mcr.microsoft.com/mssql/server:latest
          └─🔌 open 86.15.92.46:1433 -> 1433

💡 You can inspect and manage your above stack with these commands:
        monk logs (-f) local/mssql/db - Inspect logs
        monk shell     local/mssql/db - Connect to the container's shell
        monk do        local/mssql/db/action_name - Run defined action (if exists)
💡 Check monk help for more!
```

## Variables

The variables are in `stack.yml` file. You can quickly setup by editing the values here.

| Variable       | Description                | Default  |
| -------------- | -------------------------- | -------- |
| mssql_password | MSSQL SA database password | P@ssw0rd |

## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```
