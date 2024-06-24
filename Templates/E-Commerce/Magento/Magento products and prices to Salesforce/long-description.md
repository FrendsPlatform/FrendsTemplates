This template inserts and updates Magento products and their corresponding prices to Salesforce.
Using this template, you can insert your new Magento products and prices to Salesforce and update existing products' prices.

![Template](assets/Adobe_Commerce___Magento_product_and_price_to_Salesforce.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The Salesforce user should have access to client ID, secret and security token.
- Price book for Magento is initialized in Salesforce. It is labelled as "Magento Price Book" in this template.

# Implementation and Usage Notes

This template uses Salesforce queries to identify a product and the price book it's connected to. All products are checked, and if the product exists in Salesforce, the price for that item will be updated in the Magento price book with the latest information from Magento.
Standard price book status information is retrieved and compared to Magento price book name. If Magento is not the standard price book, the product data is inserted into the standard price book first. After that, the Magento price book information is retrieved for product data handling.
The price book, in which the product price is inserted or updated, can be changed by altering the name in the price book task parameters.
Process variables include fields for both Salesforce and Magento credentials.

# Error Handling

There is an error check after every task. If an error occurs during product handling, an error message is added to the exceptions variable, and the next product is taken for handling. When the process ends, error messages from related tasks and products are listed.
Transient errors are not handled. If they are expected, retries for connections with Magento and Salesforce can be enabled from the tasks.