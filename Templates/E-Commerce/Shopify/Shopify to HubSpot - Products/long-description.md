This template exports all active products from Shopify and imports them to HubSpot.
Using this template, you can insert product data from Shopify to HubSpot.

![Template](assets/Shopify_to_HubSpot_-_Products.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- Shopify access token is accessible.
- HubSpot user exists for performing the synchronization.
- HubSpot access token is accessible.
- HubSpot API has permissions to the "e-commerce" scope.

# Implementation and Usage Notes

This template uses HTTP requests GET, PATCH and POST to perform operations on both Shopify and HubSpot. GET is used to retrieve product information from Shopify. POST is used to match the search data in HubSpot with Shopify product handle and to insert new product data to HubSpot. PATCH is used to update existing products' data with the new information from Shopify.
Other operations are not performed by the template.
Process variables include base urls and access tokens for both Shopify and HubSpot.

# Error Handling

Each task is followed by an error check. If an error occurs while handling a product, the handling will stop and the next product will be taken for handling. All encountered errors will be appended to the exception variable and shown at the end of the process.
If transient errors are expected, retries for HubSpot and Shopify connections can be enabled from the tasks. Transient errors are not handled.
