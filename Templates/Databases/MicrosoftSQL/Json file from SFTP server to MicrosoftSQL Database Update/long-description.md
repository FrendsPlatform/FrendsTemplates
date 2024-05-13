This process will read a **JSON** file, which contains key-value pairs representing the data to update the specified table in the **Microsoft SQL database**, from an **SFTP server**. 

![Template](assets/Json_file_from_SFTP_server_to_MicrosoftSQL_Database_Update.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The **SFTP server** user should have the permissions to connect and access 
  the files that **Frends** needs to download.
- The **Frends** agent has access to **Microsoft SQL database** where the data will be updated and the necessary permissions to perform the updated.

# Implementation and Usage Notes

This template only performs updates into the **Microsoft SQL database** table specified in the Process Variables.
This process will read a **JSON** file from an **SFTP server**, which contains key-value pairs representing the data and update the specified table in the **Microsoft SQL database**. 

**Example Json data**

```
[
	{
		"RateKey": "EURUSD",
		"Currency": "USD",
		"Rate": 1.05,
		"RateDate": "2024-03-20 12:12:04.000",
		"Where": "RateKey = 'EURUSD'"
	},
	{
		"RateKey": "EURGBP",
		"Currency": "GBP",
		"Rate": 1.05,
		"RateDate": "2024-03-20 12:12:04.000",
		"Where": "RateKey = 'EURGBP'"
	},
	{
		"RateKey": "EURDKK",
		"Currency": "DKK",
		"Rate": 1.05,
		"RateDate": "2024-03-20 12:12:04.000",
		"Where": "RateKey = 'EURDKK'"
	},
	{
		"RateKey": "EURJPY",
		"Currency": "JPY",
		"Rate": 1.05,
		"RateDate": "2024-03-20 12:12:04.000",
		"Where": "RateKey = 'EURJPY'"
	}
]
```

# Error Handling

This template does not handle transient errors separately, however the connection
to the **SFTP server** and **MicrosoftSQL database** are retried three time before failing.

The template does not handle any SQL errors that may occur - these will be thrown as exceptions.
