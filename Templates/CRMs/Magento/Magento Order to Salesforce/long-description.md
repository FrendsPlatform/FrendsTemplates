This template exports Orders from Magento and imports them to Salesforce.
Using this template, you can insert Order and Order Products data from Magento to Salesforce.

![Template](assets/Adobe_Commerce___Magento_Order_to_Salesforce.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The Salesforce user should have access to client ID, secret and security token.
- Magento Customer has been added as a Contact in Salesforce with Account information.

# Implementation and Usage Notes

This template uses Salesforce queries to get information about Orders, Contacts and Price Books.
Process variables include fields for Pricebook Id associated with the Salesforce Order, and credentials for both Salesforce and Magento.

# Error Handling

Error handling is not implemented in this template.
However, if transient errors are expected, retries for Salesforce and Magento connections can be enabled from the tasks.