Template enables to convert Json file into Csv file. Both source file needs to be on an SFTP server, while target file will be stored in same or other SFTP server.

![Template](assets/simplified_template.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The Source SFTP server user should have read access to files
- The Target SFTP server user should have write access to files

# Implementation and Usage Notes

This template create new Csv file based on data provided by Json file. It doesn't make any changes to Json file. In case of already existing file in Target path, old file will be overwritten. Csv file

# Error Handling

Connection to both SFTP servers is retried three time before failing. Any other error related to conversion process is not handled by custom exception.
