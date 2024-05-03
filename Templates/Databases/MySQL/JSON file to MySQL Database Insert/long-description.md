This process will read a **Json file**, which contains key-value pairs representing the data to INSERT into the specified table in the database, from an **SFTP server**. 



![Template](assets/Json file to MySQL Database Update.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The SFTP server user should have the permissions to connect and access 
  the files that Frends needs to download.
- The Frends agent has access to the MySQL database where the data will be inserted and the necessary permissions to perform the insert.

# Implementation and Usage Notes

This template only performs INSERTs into the database table specified in the Process Variables.
The input Json file will contain the data to be inserted in key-value format, it can contain any column names from the table that is to be updated.

**Exampls Json data**
[
	{
		"email": "dave121@example.com",
		"address1": "91441 River Drive",
		"address2": " #1901",
		"country": "USA",
		"state": "CA",
		"city": "Rivertown",
		"zipcode": "123451",
		"phone": "1234567891",
		"firstname": "Dave",
		"lastname": "Twenty-One",
		"title": "Mr"
	},
	{
		"email": "dave221@example.com",
		"address1": "91442 River Drive",
		"address2": " #1902",
		"country": "USA",
		"state": "CA",
		"city": "Rivertown",
		"zipcode": "123452",
		"phone": "1234567892",
		"firstname": "Dave221",
		.....
		.....
]		
		
# Error Handling

This template does not handle transient errors separately, however the connection
to the SFTP server and Database are retried three time before failing.

The template does not handle any SQL errors that may occur.
