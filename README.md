# Cisco-Unified-Communications-CUCM
Scripts for managing Cisco Unified Communications Manager

This script is designed for continuous monitoring of configuration changes in Cisco Unified Communications Manager and emails admin team with the change details, if the change is detected, which is different from the standard base config that was configured during the initial installation. The admin can then review the change and commit, if it was intentional or revert if it was for testing or accidental change.

**Code Base Logic**
The script uses the CUCM AXL List Change API to monitor for any changes in the dataase. List change API provides the following details if there are any changes in the system.
  action - indicates the type change: u is update, a is add, r is remove
  

Upon receiving the change details, based on the changed config name, action and the change details the script pulls the complete configuration details from CUCM using sql query and updates the corresponding running configuration file and emails the admin team notifiying the changed item and the procedure to commit the change to the base config.

**Requirements**


