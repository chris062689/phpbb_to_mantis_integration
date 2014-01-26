phpbb to mantis integration
=============

Modified core mantis files to add support for phpbb integration.

About This Project
-----------
This project is designed to keep the phpbb and mantis user tables in synchronization with one another.
Currently, a one-way push from phpbb to mantis is supported.

This integration uses triggers on the phpbb_user table for UPDATE and INSERT statements.

This allows for the following:
  * Create the mantis user when the phpbb user is created.
  * Update the mantis user's email when it's changed in phpbb.
  * Keep the user's password in sync; adds support for phpBB's password cryptography.   
  
  
Requirements
-----------
The following are requirements in order to use the integration:
  * phpBB installed  (version: 3.0.12)
  * mantis installed (version: 1.2.15)
  * By default, the triggers assume both phpbb and mantis are installed in the same database.
  * By default, the triggers assume phpbb has read-write access to the mantis_user_table table.

Installation
-----------
1. Add the following to your config_inc.php file.
   ```$g_phpbb_integration = ON;```
2. Execute the SQL file Triggers.sql on the target database.
3. Copy the mantis folder into your web directory, overwriting the existing mantis folder.
   [If you have made any additional code changes to these files, you must merge your custom code changes.]

Validation
-----------
To validate the integration is successfully installed, change your password on your phpbb account, and attempt to login to mantis using the same credentials. 
If login has failed:
  * Verify the passwords match in both the mantis and phpbb user tables.
  * Verify the triggers are active (update email on phpbb and verify that changes in mantis)

