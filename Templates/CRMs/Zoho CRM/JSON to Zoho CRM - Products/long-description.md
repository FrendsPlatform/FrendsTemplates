This template process reads a JSON file containing product data and either inserts or updates the products into Zoho CRM.

![Template](assets/JSON-to-Zoho-CRM-Products.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- You have a refresh token for the Zoho API. One can be created using the corresponding template.
- The client ID and client secret for Zoho are available.
- It is known which domain your Zoho instance is in, e.g., EU or America.
- The Frends agent has access to the folder from which the JSON file should be read.

# Implementation and Usage Notes

This template reads product information from a JSON file and inserts or updates the products into Zoho CRM. To determine if a product should be inserted or updated, the product codes of the existing products on Zoho CRM are compared to the codes of the products to be inserted or updated.

This template assumes that the input JSON structure is correct and uses the field names that the Zoho API expects. The template does not perform any mapping for the JSON data.

The process variables include the regional domain URLs for your Zoho instance, the client ID and secret for Zoho, the refresh token for the Zoho API, and the path to the input JSON file in the local fileshare.

**Sample input JSON structure**

```json
[
  {
    "Product_Category": "Example category",
    "Qty_in_Demand": 10,
    "Description": "This is an example product.",
    "$currency_symbol": "$",
    "Product_Active": true,
    "Product_Code": "JSON1",
    "Manufacturer": "Test Corp",
    "Product_Name": "Example product 1",
    "Qty_Ordered": 10,
    "Qty_in_Stock": 100,
    "Unit_Price": 1500,
    "Reorder_Level": 10
  },
  {
    "Product_Category": "Example category",
    "Qty_in_Demand": 13,
    "Description": "This is an example product.",
    "$currency_symbol": "$",
    "Product_Active": true,
    "Product_Code": "JSON2",
    "Manufacturer": "Test Corp",
    "Product_Name": "Example product 2",
    "Qty_Ordered": 5,
    "Qty_in_Stock": 88,
    "Unit_Price": 125,
    "Reorder_Level": 10
  },
.
.
.
]
```

In addition to the fields shown in the example JSON, this template supports all other fields that the Zoho API supports, given that the field names are given correctly.

# Error Handling

This template checks for errors after each task. If handling the input JSON, or creating an API access token fails, the process throws an exception. If inserting or updating a single product fails, an error message is added to the error variable whose value is printed at the end of the process.

If transient errors are expected, retries for the Zoho API connections or the file handling can be configured in the corresponding tasks.