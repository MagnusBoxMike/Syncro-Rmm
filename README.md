# Syncro-Rmm

These scripts have been created to work with Magnus Box and Syncro RMM. We are posting the different scripts here to allow us to maintain version control and ease of accesability.

Before implementing these scripts, please open a ticket by emailing support@magnusbox.com. You can put "Syncro" in the subject line. The reason for this is to allow us to setup the dedicated API user account on your Magnus Box server.

As always, never run a script without understanding how it works. You take full responsibility for running these scripts on your clients endpoints.

Interested in Magnus Box? Visit www.magnusbox.com for more information.

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
4. Input a secure username and password in the "Magnus Box Password" & "Magnus Box Username" fields 
  -  <b>Note</b>: The password for the user can NOT contain special characters. Otherwise, it is unable to remotely log in to Magnus Box and will require you to manually log in the user.
5. Repeat this process for every customer that you would like to add to Magnus Box. 

You will also need a dedicated Magnus Box API account setup for Syncro. You will use this to run the scripts. To have a dedicated API account setup, please email support@magnusbox.com and request a Syncro API user account.

# Scripts

<strong>Script Name</strong> - Create New User

<strong>Usage</strong> - This script is used to create a new client backup account on your Magnus Box server from within the Syncro RMM dashboard. It also has the ability to assign a storage vault and policy if desired. The policy must be set as the default within the web dashboard.

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
21. Set the "$AssignPolicy" and "$AssignVault" to "$false" to disable auto-selecting of a vault and policy (they are set to $true by default)
22. Modify the "Server" section with the url of your Magnus Box server. Ex. app.magnusbox.com. Do not include the HTTP or www
23. Do not modify anything below the line "# --- DO NOT MODIFY ANYTHING BELOW THIS LINE ---"
24. Click "Create Script"
25. You can now run this script to create user accounts on your Magnus Box server.

<br><br>

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
9. Under "Variable Type", select "Runtime"
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
22. You can now run this script to delete user accounts on your Magnus Box server. Use as a LAST resort as this script removes ALL backup data for the selected users. You will be required to enter in the username of the user you want to delete as an added safety precaution.

<br><br>

<strong>Script Name</strong> - Silent Install

<strong>Usage</strong> - This script will silently install the backup software on a user's computer.

<strong>Instructions</strong>

1. Login to your Syncro portal
2. Go to scripts
3. Click on "New Script"
4. Name the script "Magnus Box - Silent Install" (or any other descriptive title)
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
16. Pull up the Github script for "Silent Install"
17. Copy or click the "raw" button and copy/paste the entire script to the Script section of Syncro
18. Within the script, modify the "$backupname" variable to reflect the exact spelling of your software's name (i.e. "Magnus Box Devops")
   - Can be found from the Desktop Icon name or by contacting Magnus Box for support
19. Within the script, modify the second variable, "$server", to match your web portal URL, excluding /'s and https:// (i.e. devops.magnusbox.com)
20. Do not modify anything below the line "# --- DO NOT MODIFY ANYTHING BELOW THIS LINE ---"
21. Click "Create Script"
22. You can now run this script to install the backup software silently for each user. It will take approximately 60 seconds. After the install, you should be able to view the device and set up the Protected Items.

<br><br>

<strong>Script Name</strong> - Silent Uninstall

<strong>Usage</strong> - Use this script to silently uninstall the backup software without interrupting the user

<strong>Instructions</strong>

1. Login to your Syncro portal
2. Go to scripts
3. Click on "New Script"
4. Name the script "Magnus Box - Silent Uninstall" (or any other descriptive title)
5. For the "File Type", select "PowerShell" from the dropdown menu
6. For "Run as" and "Max Script Run Type", keep them as the default values ("System" and "10" respectively)
7. Pull up the Github script for "Silent Uninstall"
8. Copy or click the "raw" button and copy/paste the entire script to the Script section of Syncro
9. Within the script, modify the "$backupname" variable to reflect the exact spelling of your software's name (i.e. "Magnus Box Devops")
   - Can be found from the Desktop Icon name or by contacting Magnus Box for support
10. Do not modify anything below the line "# --- DO NOT MODIFY ANYTHING BELOW THIS LINE ---"
11. Click "Create Script"
12. You can now run this script to uninstall the backup software silently for each user. After uninstalling, make sure to <strong>delete the user account</strong>. You will continued to be billed unless the user is removed!
   - To remove a user, navigate to the web portal. Go to Accounts --> Users. Find and click the affected user. In the upper right corner, click Actions --> Delete to remove the user.
   - Contact Magnus Box for additionall support or if any questions arise

<br><br>

<strong>Script Name</strong> - Remove Icon

<strong>Usage</strong> Will remove the desktop icon for the user's computer, but it will not remove the backup software

<strong>Instructions</strong>

1. Login to your Syncro portal
2. Go to scripts
3. Click on "New Script"
4. Name the script "Magnus Box - Remove Desktop Icon" (or any other descriptive title)
5. For the "File Type", select "PowerShell" from the dropdown menu
6. For "Run as" and "Max Script Run Type", keep them as the default values ("System" and "10" respectively)
7. Pull up the Github script for "Remove Icon"
8. Copy or click the "raw" button and copy/paste the entire script to the Script section of Syncro
9. Within the script, modify the "$backupname" variable to reflect the exact spelling of your software's name (i.e. "Magnus Box Devops")
   - Can be found from the Desktop Icon name or by contacting Magnus Box for support
10. Do not modify anything below the line "# --- DO NOT MODIFY ANYTHING BELOW THIS LINE ---"
11. Click "Create Script"
12. You can now run this script to remove the icon from the user's desktop.

