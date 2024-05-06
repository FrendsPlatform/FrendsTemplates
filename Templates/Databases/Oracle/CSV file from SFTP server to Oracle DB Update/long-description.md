This process will connect to an SFTP server and read a CSV file, which contains the data to UPDATE in the specified table in the Oracle database.

![Template](assets/CSV_file_from_SFTP_server_to_Oracle_DB_Update.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The SFTP server user should have the permissions to connect and access 
  the files that Frends needs to download.
- The Frends agent has access to the Oracle database where the data will be updated and the necessary permissions to perform the update.
- The CSV column names are the same as the column names in the Oracle database table.

# Implementation and Usage Notes

This template only performs UPDATEs into the Oracle database table specified in the Process Variables.

The input CSV file must contain the data to be updated and can contain any column names from the Oracle database table.

**Example CSV data**

```
email;state;phone
dave21@frends.com;CA;123456789
dave51@frends.com;NH;123456789
dave52@frends.com;NY;123456789
dave53@frends.com;NY;123456789
```

# Error Handling

This template does not handle transient errors separately, however the connection to the SFTP server and MySQL database are retried three time before failing.

The template does not handle any SQL errors that may occur - the errors will be thrown as exceptions.
