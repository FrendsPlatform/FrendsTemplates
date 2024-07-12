This template parses your local Excel files and imports them to your Microsoft SQL database table.

Using this template, you can insert any kind of data from your Excel files to the Microsoft SQL table.

![Template](assets/Local_Excel_to_Microsoft_SQL.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- Microsoft SQL table exists for performing the synchronization.
- Microsoft SQL connection string is accessible.
- The Excel file content is in the same structure as the database table columns.
- If there are multiple Excel files in the local folder, all files should be in the same structure.

# Implementation and Usage Notes

This template will locate Excel files in the local folder provided in the process variable. Each file is then parsed to a DataSet. DataSet table contents are transformed to a JSON string and inserted to the Microsoft SQL table. The local Excel files are not manipulated in any way by this template.

Excel files should not include headers - only the data to be inserted is required. The Excel file should be structured in the same way as the database or vice versa.

Process variables include the path name to the local folder, the Microsoft SQL table name and the connection string for Microsoft SQL.

# Error Handling

Each task is followed by an error check. If an error occurs when handling a file, that file's data won't be uploaded and the next file will be taken for handling. Any errors encountered will be noted at the end of the process.
If transient errors are expected, retries can be enabled from the tasks. Transient errors are not handled.