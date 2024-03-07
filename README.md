# Frends Integration Process Templates

This repository contains a collection of process templates for the Frends integration platform. These templates are designed to provide a starting point for common integration scenarios, reducing the time and effort required to set up new integrations.

Each template includes a detailed description of its purpose, instructions for use, and a sample configuration. They are designed to be easily customizable to fit your specific integration needs.

Whether you're integrating databases, APIs, or other systems, these templates can help streamline your integration process on the Frends platform.

# Structure

NB! This is preliminary!

The templates are arranged by category. 

- README.md
- Templates
  - Category 1
    - Template 1
    - Template 2
  - Category 2
    - Template 3
    - Template 4
  - Category 3
    - Template 5
    - Template 6

Each template folder has the following files:

- **long-description.md** - contains full template description along with intro, usage, configuration options and any other relevant information. This is used by the Template Portal.- **assets/*** - this folder can contain any images or assets used in the *long-description.md* file.
- **short-description.md** - contains short and simple description of the template. This is used by Frends in process/template description.
- **process.json** - the template itself
- **metadata.json** - the template metadata, including its name, version and any integrated systems, that cannot be deducted by looking at the tasks used in the process.

Metadata.json contents
```
{ 
  "name": "Excel to Gmail",
  "version": "1.0.1",
  "tags": [
    "AWS",
    "Cloud",
    "Storage"
  ],
  "additionalSystemsUsed": [
    "System1",
    "System2"
  ]
}
```

Please note that the metadata.json that will be packaged for Frends and Template portal will be different from the above metadata, because we will need to extract some data from template. This however will be done at build time, and the approximate final metadata will look approximately like this:

```
{ 
  "name": "Excel to Gmail",
  "version": "1.0.1",
  "tags": [
    "AWS",
    "Cloud",
    "Storage"
  ],
  "additionalSystemsUsed": [
    "System1",
    "System2"
  ],
  "tasks": [
     "Frends.AmazonS3.Upload",
     "Frends.Gmail.SendEmail"
  ],
  "downloadUrl": "xxx",
  "githubUrl": "yyy",  
}
```
