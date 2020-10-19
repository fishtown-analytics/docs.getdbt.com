---
title: "Microsoft Azure Synapse DW Profile"
---


:::info Community contributed plugin

These are Community Contributed plugins for dbt. If you're interested in contributing, check out the source code for each repository:
- [`dbt-synapse`](https://github.com/swanderz/dbt-synapse)
- [`dbt-azuresynapse`](https://github.com/embold-health/dbt-azuresynapse)

:::

## Overview of dbt-synapse
**Status:** Community Contributed

**Author:** Nandan Hegde and Anders Swanson

**Source Code:** https://github.com/swanderz/dbt-synapse

**dbt support**: version 0.18.0 and newer

The pacakge can be installed from PyPI with:

```python
pip install dbt-synapse
```
For further (and more likely up-to-date) info, see the [README](https://github.com/swanderz/dbt-synapse/blob/master/README.md)

### Connecting to SQL Server with **`dbt-azuresynapse`**

the following is needed for every target definition for both SQL Server and Azure SQL.  The sections below details how to connect to SQL Server and Azure SQL specifically.
```
type: sqlserver
driver: 'ODBC Driver 17 for SQL Server' (The ODBC Driver installed on your system)
server: server-host-name or ip
port: 1433
schema: schemaname
```
### standard SQL Server authentication
SQL Server credentials are supported for on-prem as well as cloud, and it is the default authentication method for `dbt-sqlsever`
```
user: username
password: password
```
### Azure SQL-specific auth
The following [`pyodbc`-supported ActiveDirectory methods](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#new-andor-modified-dsn-and-connection-string-keywords) are available to authenticate to Azure SQL:
- ActiveDirectory Password
- ActiveDirectory Interactive
- ActiveDirectory Integrated
- Service Principal (a.k.a. AAD Application)
- ~~ActiveDirectory MSI~~ (not implemented)

#### ActiveDirectory Password 
Definitely not ideal, but available
```
authentication: ActiveDirectoryPassword
user: bill.gates@microsoft.com
password: i<3opensource?
```
#### ActiveDirectory Interactive (*Windows only*)
brings up the Azure AD prompt so you can MFA if need be.
```
authentication: ActiveDirectoryInteractive
user: bill.gates@microsoft.com
```
#### ActiveDirectory Integrated (*Windows only*)
uses your machine's credentials (might be disabled by your AAD admins)
```
authentication: ActiveDirectoryIntegrated
```
##### Service Principal
`client_*` and `app_*` can be used interchangeably
```
tenant_id: ActiveDirectoryIntegrated
client_id: clientid
client_secret: ActiveDirectoryIntegrated
```


## Overview of dbt-azuresynapse
**Status:** Community Contributed

**Author:** Ernesto Barajas and Matt Berns

**Source Code:** https://github.com/embold-health/dbt-azuresynapse

**dbt-azuresynapse**
Only supports dbt 0.17 and newer!

Easiest install is to use pip:

    pip install dbt-azuresynapse

On Ubuntu make sure you have the ODBC header files as well as the appropriate ODBC adapter before installing

    sudo apt install unixodbc-dev
    sudo apt-get install msodbcsql17
    sudo apt-get install mssql-tools

### Connecting to SQL Server with **dbt-azuresynapse**

#### User / password authentication

Configure your dbt profile for using SQL Server authentication or Integrated Security:

##### SQL Server authentication
```yaml
dbt-azuresynapse:
  target: dev
  outputs:
    dev:
      type: azuresynapse
      driver: 'ODBC Driver 17 for SQL Server' (The ODBC Driver installed on your system)
      server: server-host-name or ip
      port: 1433
      user: [username]
      password: [password]
      database: [databasename]
      authentication: SqlPassword
      schema: [schema]
```