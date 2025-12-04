# Cisco-Unified-Communications-CUCM
Scripts for managing Cisco Unified Communications Manager

This script is designed for continuous monitoring of configuration changes in Cisco Unified Communications Manager and emails admin team with the change details, if the change is detected, which is different from the standard base config that was configured during the initial installation. The admin can then review the change and commit, if it was intentional or revert if it was for testing or accidental change.

**Code Base Logic**
The script uses the CUCM AXL List Change API to monitor for any changes in the dataase. List change API provides the following details if there are any changes in the system.
  action - indicates the type change: u is update, a is add, r is remove
  doGet - Boolean value indicates when the client should perform a get operation to get the full details of the object.
  type - Changed configuration item. Ex: DevicePool, RoutePattern, TransPattern.
  ChangedTags - Contains name of the configuration field that was changed and the changed value. For example, Changed Configuration field is Description and the value is "Jon Doe".
  Based on the action keyword, it can be determined whether this was the new add or update or remove.

Here is the sample output, which indicates that the new routepattern was added, routelist was updated, devicepool name was changed and provides the old value and new value. UUID field indicates the unique identifier of the each configuration item. This UUID field is being used to retrieve the new config from CUCM and update the running config file.

  <img width="1386" height="614" alt="image" src="https://github.com/user-attachments/assets/3835bc35-93a6-4ab2-ba25-72cf533a894e" />

Upon receiving the change details, based on the type, action and the change details the script pulls the complete configuration details from CUCM using sql query and updates the corresponding running configuration file and emails the admin team notifiying the changed item and the procedure to commit the change to the base config.

**Requirements**


