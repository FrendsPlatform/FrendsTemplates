This template fetches customers from Adobe Commerce / Magento and inserts or updates them to Zoho CRM as contacts.

Using this template you can synchronize customers from Adobe Commerce / Magento to Zoho CRM.

![Template](assets/Adobe_Commerce___Magento_to_Zoho_CRM_-_Customers.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The Magento user should be eligible to obtain an admin authorization token from Magento.
- The Zoho CRM refresh token should be provided as a process variable.

# Implementation and Usage Notes

The access tokens to both Magento and Zoho CRM are retrieved first. The required credentials to obtain the tokens should be provided in process variables.

This template fetches all customers from Magento and either inserts or updates them as contacts in Zoho CRM. To determine if a Magento customer already has a corresponding contact in Zoho CRM, the email addresses of the Magento customers are compared to those of the existing contacts in Zoho CRM.

Customers that have been deleted from Magento are not transferred.

Process variables include credentials and URLs for connecting to both Magento and Zoho CRM.

# Error Handling

This template checks for errors after every task. Errors during customer handling are stored in the exception variable. If, for example, a customer is unable to be inserted to Zoho CRM, the execution proceeds to the next customer and an error message is added to the exception variable. The exception variable is then printed at the end of the process.

Transient errors are not handled separately. If they are expected, retries for connections to Magento and Zoho CRM can be enabled from the tasks.