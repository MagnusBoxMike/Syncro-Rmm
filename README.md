# Syncro-Rmm

These scripts have been created to work with Magnus Box and Syncro RMM. We are posting the different scripts here to allow us to maintain version control and ease of accesability.

Before implementing these scripts, please open a ticket by emailing support@magnusbox.com. You can put "Syncro" in the subject line. The reason for this is to allow us to setup the dedicated API user account on your Magnus Box server.

As always, never run a script without understanding how it works. You take full responsibility for running these scripts on your clients endpoints.

Interested in Magnus Box. Visit www.magnusbox.com for more information.

# Setting up in Syncro

These scripts require the use of the custom customer fields in Syncro. 

<strong>Here is how to set this up:</strong>

1. Login to your Syncro Portal
2. Go to the admin tab
3. Scroll down to the Customers section and click "Customer Custom Fields"
4. Click on "New Field" 
5. Type "Magnus Box Password" in the name field
6. Select "Text Field" in field type and clik "Create Customer Field"
7. Click on "New Field" again and this time type "Magnus Box Username" in the name field
8. Select "Text Field" in field type and clik "Create Customer Field"

<strong>Now you can create the username and passwords for the Magnus Box platform in Syncro.</strong>

1. Click on Customers
2. Select a customer
3. Under custom fields, click edit
4. Inpute a secure username and password in the "Magnus Box Password" & "Magnus Box Username" fields 
5. Repeat this process for every customer that you would like to add to Magnus Box. 

You will also need a dedicated Magnus Box API account setup for Syncro. You will use this to run the scripts. To have a dedicated API account setup, please email support@magnusbox.com and request a Syncro API user account.

# Scripts

<strong>Script Name</strong> - Create New User

<strong>Usage</strong> - This script is used to create a new client backup account on your Magnus Box server from within the Syncro RMM dashboard.

<strong>Instructions</strong>

1. Login to your Syncro portal
2. Go to Scripts
3. Click on New Script
4. Name the script "Magnus Box - Create New User" or whatever you would like
5. Check the "Mark as Favorite" box. Mainly because this will be one of your favorite scripts.
6. Under "File Type" select "PowerShell" from the drop down menu
7. Now click on "Add Script Variable"
8. Under "Variable Name -$" name it "mbu"
9. Under "Variable Type" select "Platform"
10. The "Value" box should now appear.
11. In the "Value" box, select "{{customer_custom_field_magnus_box_username}} -"
12. Now we need to add the next variable. Click on "Add Script Variable"
13. Under "Variable Name -$" name it "mbp"
14. Under "Variable Type" select "Platform"
15. The "Value" box should now appear.
16. In the "Value" box, select "{{customer_custom_field_magnus_box_password}} -"
17. Leave the "Run as" box as "System" and the "max Script Run Time" box as "10"
18. Pull up the Github script for Create New User
19. Copy or click the "raw" button and copy/paste the script entirely to the Script section of Syncro
20. From within the script, modify the "User", "Password" section with the API user account info provided my Magnus Box
21. Modify the "Server" section with the url of your Magnus Box server. Ex. app.magnusbox.com. Do not include the HTTP or www. 
22. Do not modify anything below the line "# --- DO NOT MODIFY ANYTHING BELOW THIS LINE ---"
23. Click "Create Script"
24. You can now run this script to create user accounts on your Magnus Box server.



<strong>Script Name</strong> - Delete User

<strong>Usage</strong> - This script is used to remove a user account and disable their login credential from the Syncro RMM Dashboard. <strong>WARNING: This will permanently remove the user and ALL DATA associated with the user's backups.</strong>

<strong>Instructions</strong>

1. Login to your Syncro portal
2. Go to scripts
3. Click on "New Script"
4. Name the script "Magnus Box - Delete User Account" (or any other descriptive title)
5. For the "File Type", select "PowerShell" from the dropdown menu
6. For "Run as" and "Max Script Run Type", keep them as the default values ("System" and "10" respectively)
7. Click on "Add Script Variable"
8. Under "Variable Name -$", enter "mbu"
9. Under "Variable Type", select "Platform"
10. In the "Value" field, select "{{customer_custom_field_magnus_box_username}} -"
11. Add a second variable:  Click "Add Script Variable"
12. Under "Variable Name -$" name it "mbp"
13. Under "Variable Type" select "Platform"
14. The "Value" box should now appear.
15. In the "Value" box, select "{{customer_custom_field_magnus_box_password}} -"
16. Pull up the Github script for "Delete User"
17. Copy or click the "raw" button and copy/paste the script entirely to the Script section of Syncro
18. From within the script, modify the "User", "Password" section with the API user account info provided by Magnus Box
19. Modify the "Server" section with the url of your Magnus Box server. Ex. app.magnusbox.com. Do not include the HTTP, www, or /'s. 
20. Do not modify anything below the line "# --- DO NOT MODIFY ANYTHING BELOW THIS LINE ---"
21. Click "Create Script"
22. You can now run this script to delete user accounts on your Magnus Box server. Use as a LAST resort as this script removes ALL backup data for the selected users.


<strong>Script Name</strong> -Silent Install

<strong>Usage</strong> Coming Soon

<strong>Instructions</strong> Coming Soon

<strong>Script Name</strong>- Silent Uninstall

<strong>Usage</strong> Coming Soon

<strong>Instructions</strong> Coming Soon

<strong>Script Name</strong>- Remove Icon

<strong>Usage</strong> Coming Soon

<strong>Instructions</strong> Coming Soon
