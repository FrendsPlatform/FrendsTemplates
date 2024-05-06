This process will connect to an SFTP server and read a JSON file, which contains key-value pairs representing the data to INSERT into the specified table in the database.

![Template](assets/JSON_file_from_SFTP_to_MySQL_Database_INSERT.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The SFTP server user should have the permissions to connect and access 
  the files that Frends needs to download.
- The Frends agent has access to the MySQL database where the data will be inserted and the necessary permissions to perform the insert.
- JSON file structure is not nested and the keys are the same as the column names in the database table.

# Implementation and Usage Notes

This template only performs INSERTs into the database table specified in the Process Variables.

The input JSON file must contain the data to be inserted in key-value format, it can contain any column names from the MySQL table.

**Example JSON data**

```
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
		"lastname": "Twenty-One",
		"title": "Mr"
	}
]
```

# Error Handling

This template does not handle transient errors separately, however the connection to the SFTP server and MySQL database are retried three time before failing.

The template does not handle any SQL errors that may occur - the errors will be thrown as exceptions.
