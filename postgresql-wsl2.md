## PostgreSQL WSL2 setup:

### Installation instructions:

Taken from the [Microsoft Docs](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-database). Refer to the official docs for latest info.

### Configuration instructions:

Taken from this [blog post](https://www.cybertec-postgresql.com/en/postgresql-on-wsl2-for-windows-install-and-setup/). Refer to the official docs for latest info.

### Start/Stop server in wsl:

• `sudo service postgresql start`
• `sudo service postgresql stop`
• `sudo service postgresql status`

### Connect to postgresql command line:

• `sudo -u postgres psql`
• `psql -U gagan -d postgres`

### GENERAL COMMANDS:

• Show all roles/users: `\du`
• Connection info: `\conninfo`
• Create a new role `CREATE ROLE <name> WITH <options> ;`
` CREATE ROLE benjamin WITH SUPERUSER; `
• Drop a role `DROP ROLE benjamin;`
• Show a list of all databases `\l`
