This file provides information on setting up the IOT2020 device and required software.

You will need software to flash a microSD card. You will need WinSCP and PuTTY software to communicate with the device.

1. Flash the SD card with the most recent software provided by siemens.
The most recent software for the IOT2020 can be found at - https://support.industry.siemens.com/cs/document/109741799/simatic-iot2000-sd-card-example-image?dti=0&lc=en-WW (an account is required to download)
The unzipped file should be flashed to the root directory of the SDcard.

2. Insert the SD card into the IOT2020 as per installation instructions.

3. Insert IOT shield into device as per installation instructions. 

4. Provide supply power to the device as per  manufacturer installation instructions.

5. Connect IOT2020 device via LAN cable to a local router, on which network a working PC can communicate with.

6. Power up the IOT2020 device, the device will automatically  boot and configure from the SD card.

7. Set up communication via WinSCP and open a PuTTY session.
    - In the command line window
        type: iot2000setup
        press enter, a setup window will appear 
    - In networking----> Configure Interfaces ----> change eth0 to dhcp, this will allow the router to provide an IP address to the device. Return to the menu
    - In software ----> Manage autostart options ----> Select all the options, this will autostart node-red, SSH server and MQTT on startup. Return to menu
    - Exit the setup window and press the restart button on the IOT2020 to restart the device and update these settings.
   
8. Re-connect to the PuTTY session. To install the required node-red packages, use the following commands:

    cd /usr/lib/node_modules/node-red/node_modules/      (this takes you to the ndoe-red modules directoroy)
    npm install node-red-contrib-iot2020          (installs iot2020 nodes)
    npm install node-red-contrib-moment
    npm install node-red-dashboard
    npm install node-red-node-sqlite
    
    once all packages are installed, reset the IOTdevice to update the packages

9. To create an SQLite database location:
    Using WinSCP, In the root directory create a folder called 'dbs'
    
    In the PuTTY window: enter the followng commands:
    cd    (returns to route directory)
    cd /dbs     (goes to database locations)
    sqlite3 sqlite.db    (creates an database in the directory called 'sqlite'
    .quit (closes the sqlite program)
    
    If you look in the DBS folder, you should now have a database.

You should now have all the pre-requisites to run the system.
To update node-red etc. there are useful turorials online.


    
    
  
