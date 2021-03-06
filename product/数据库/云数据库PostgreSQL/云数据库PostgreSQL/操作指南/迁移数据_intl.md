# Using Tencent Cloud DTS
TencentDB for PostgreSQL supports importing data using the **Data Migration** feature of **Data Transfer Service (DTS)**.

For more information, see [PostgreSQL Data Migration](https://intl.cloud.tencent.com/document/product/571)

# Using psql Command
If your data is already on PostgreSQL, you can easily migrate the data to TencentDB for PostgreSQL using the psql command.
The data migration is mainly divided into two parts:
> (1) Perform logical backup using the pg_dump command to create dump data.
> (2) Restore the backup data in the previous step to TencentDB for PostgreSQL.
Preparation: The PostgreSQL instance would have been ready. If not, see the instructions on applying for instances and connecting instances.

## Step 1
Connect to the local database using PostgreSQL client and execute the command below to back up the data.

```
pg_dump -U username -h hostname -p port -d databasename -f filename
```

Parameter description


| Parameter | Description |
|---------|---------|---------|
| username | User name of the local database |
| hostname | Host name of the local database. You can use "localhost" if you're logging in from the local database host |
| port | Port number of the local database |
| databasename | Name of the local database to be backed up |
| filename | Name of the backup file to be generated, such as mydump.sql |


## Step 2
Preparation: Upload the backup data to the CVM on the same private network and then restore the data through the private network to ensure network stability and data security.
After you log in to the CVM, run the command below in the PostgreSQL client to restore the data.

```
psql -U username -h hostname -d desintationdb -p port -f dumpfilename
```
Parameter description


| Parameter | Description |
|---------|---------|---------|
| username | Database user name of TencentDB for PostgreSQL |
| hostname | Database address of TencentDB for PostgreSQL |
| desintationdb | Database name of TencentDB for PostgreSQL |
| port | Database port number of TencentDB for PostgreSQL |
| dumpfilename | Backup file name, such as mydump.sql |


