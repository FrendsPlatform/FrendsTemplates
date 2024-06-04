This template inserts Magento Products and their corresponding prices to Salesforce.
Using this template, you can insert your new Magento Products to Salesforce.

![Template](assets/Adobe_Commerce___Magento_Product_to_Salesforce.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The Salesforce user should have access to client ID, secret and security token.
- Magento Price Book is initialized in Salesforce.

# Implementation and Usage Notes

This template uses Salesforce Queries to verify Product and Price Book as unique. Price Book, in which the Product price is inserted, can be changed by altering the Price Book task parameters.
Process variables include fields for both Salesforce and Magento credentials.

# Error Handling

Error handling is not implemented in this template.
However, if transient errors are expected, retries for connections with Magento and Salesforce can be enabled from the tasks.