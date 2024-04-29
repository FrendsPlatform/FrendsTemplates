This Process will read a file from a **local directory**, and move it without any processing to an **SFTP Server** location.

![Template](assets/Copy_a_Single_file_from_Fileshare_to_SFTP.svg)

# Prerequisites

This template assumes that the following prerequisites are in place:

- The Frends agent has access to the local fileshare where the file has been saved.
- The SFTP server user should have the permissions to connect and write the files that Frends needs to upload.

# Implementation and Usage Notes

This template only reads a file from the local fileshare and uploads it to an SFTP server.
It does not handle cleanup of the local directory, so cleaning or local file processing should be done separately.

To use the process you must first populate the process variables .....
	1.	**InFilePath** - the **Full path** of the input file to be read.
	2.	**InFileName** - the **Name** of the input file to be read.
	3.	**TargetFilePath** - the **Full path** of the target file to be read .
	4.	**TargetFileName** - the **Name** of the target file to be read .
	5.	**TargetServerAddress** - the **Address** of the target SFTP Server.
	6.	**TargetServerUser** - the **User** for the target SFTP Server.
	7.	**TargetServerPassword** - the **Password** the target SFTP Server. 

# Error Handling

This template does not handle transient errors separately, however when connecting
to the **SFTP server** it retries **three** times before failing.

This template does not handle issues with local file access separately, so
in case file read error occurs the process execution will fail with an appropriate
error message.