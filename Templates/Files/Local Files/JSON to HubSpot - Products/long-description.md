This template reads a JSON file containing product data from a local fileshare and either inserts or updates each product in HubSpot.

![Template](assets/JSON_to_HubSpot_-_Products.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The Frends agent has access to the local fileshare containing the JSON file.
- HubSpot API key is accessible.

# Implementation and Usage Notes

The path to the JSON file in the local fileshare is determined in the process variables. The template either inserts or updates each product in HubSpot, depending on whether a product with a matching stock keeping unit (SKU) is found. 

To use the template without modifications, ensure the JSON data matches the format required for creating products via the API. If the data format does not match, the template can be adjusted to include additional mapping.

**Example JSON data structure**
```
[
    {
        "properties": {
            "name": "Example Product",
            "price": "25.00",
            "hs_sku": "example-product",
            "description": "This is an example product."
        }, 
    },
    {
        "properties": {
            "name": "Another Product",
            "price": "55.00",
            "hs_sku": "another-product",
            "description": "Another product with a description."
        }
    }
]
```

# Error Handling

If the file cannot be read, the process throws an exception. The API calls to HubSpot are checked for errors. If processing a product fails, the template moves to the next one, and any encountered errors are displayed at the end of the process. This template does not handle transient errors separately. However, if transient errors are expected, you can enable the "Retry on Failure" option in the advanced settings of the HubSpot request tasks.
