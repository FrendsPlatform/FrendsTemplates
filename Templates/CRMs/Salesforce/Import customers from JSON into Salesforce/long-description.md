This template process reads customer information from a **JSON** file in the local fileshare and creates or updates the customers in **Salesforce** as contacts.
Using this template, you can insert or update customers into Salesforce as contacts.

![Template](assets/Import_customers_from_JSON_into_Salesforce.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The Salesforce user should have access to the client ID, secret and security token.

# Implementation and Usage Notes

This template reads a JSON file from the local fileshare containing customer data and creates or updates the customers as contacts into Salesforce.
Process variables include fields for the Salesforce credentials and the path to the input file.

**Sample JSON data:**

```json
[
    {
        "email": "customer.one@example.com",
        "fax": "12345678",
        "firstname": "First",
        "lastname": "Customer",
        "city": "Helsinki",
        "country": "Finland",
        "postalcode": "00100",
        "street": "Example Street 1",
        "other_city": "Espoo",
        "other_country": "Finland",
        "other_postalcode": "02250",
        "other_street": "Example Lane 5",
        "other_phone": "1122334455",
        "mobilephone": "0033445566",
        "phone": "0022334455",
        "salutation": "Mrs.",
        "title": "CEO",
        "description": "This is a very important customer.",
        "assistantname": "Mr. Smith",
        "assistantphone": "0044332211"
    },
    {
        "email": "customer.two@example.com",
        "fax": "87654321",
        "firstname": "Second",
        "lastname": "Customer",
        "city": "London",
        "country": "United Kingdom",
        "postalcode": "12345",
        "street": "Example Lane 3",
        "mobilephone": "+123123213",
        "phone": "+321321321",
        "salutation": "Dr.",
        "title": "Vice President",
        "description": "This is a business partner.",
        "assistantname": "Ms. Green",
        "assistantphone": "0011223344"
    }
]
```

# Error Handling

This template checks for errors after each task, and proceeds accordingly. If an error is encountered when e.g., creating a contact into Salesforce, the process moves on to the next customer and an error message is appended to the error variable which is displayed at the end of the process.
If transient errors are expected, retries for the file read and Salesforce connections can be configured in the tasks.