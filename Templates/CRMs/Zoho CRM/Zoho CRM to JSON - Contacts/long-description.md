This template retrieves contact data from Zoho CRM and downloads it to a local fileshare as a single JSON file.

![Template](assets/Zoho_CRM_to_JSON_-_Contacts.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- Zoho CRM client ID and client secret should be accessible and provided in the process variables to create the refresh token.
- Zoho CRM refresh token has been generated and provided in the process variables. A refresh token can be generated with the corresponding template.
- Zoho CRM regional instances for account and API are known, and the domains are adjusted accordingly.
- The Frends agent has access to the local fileshare to which the resulting JSON file will be saved.
- The directory for the local JSON file exists.

# Implementation and Usage Notes

This template requires a refresh token for the Zoho API in order to work. The template will use the refresh token to create the access token for accessing the API. The refresh token can be created using the "Zoho CRM - Exchange grant token for refresh token" template. For this template, the token should have the following scope included: **ZohoCRM.modules.contacts.READ**.

Zoho CRM API access token is retrieved via HTTP Request. The contacts are retrieved from Zoho CRM API with the API access token. Because the contacts are paginated, a while-loop is used to go through all the pages. By default, the API will provide 200 records per page.

After processing all the contact records, the contact data is written to a single JSON file as a JSON string. The full path where the file is saved, including the file name, is determined in the process variables. If a file with the same name exists in the specified path, the file will be overwritten. This behaviour can be changed in the task settings.

# Error Handling

If retrieving the access token or contacts from Zoho CRM fails, the template will throw an exception stating the error message and no file will be written. If an error occurs with writing the JSON file, e.g. because the directory can't be found, the task will throw an exception.

Transient errors are not handled. If they're expected, retries for connections to Zoho CRM can be enabled from the tasks.
