##############################################################################################################################################
Thread Programming and Device driver in Zephyr RTOS ---------------------------------------------------------------------------------------------------------------------------------------------- 
NAME: ARJUN BHATNAGAR      
ASU ID: 1215353243         
----------------------------------------------------------------------------------------------------------------------------------------------

Please follow the following procedure to run our application:

Step 1: In the folder you will find the files assgn_02.patch and Assgn02_Report.pdf.

Step 2: Apply the patch to a new zephyr source using "patch -p4 < patch_file.patch". The previous patches are considered to be applied.
        The patch contains only source code changes for this project.

Step 3: Open terminal set environment variables as following:
        
        "export $ZEPHYR_TOOLCHAIN_VARIANT=zephyr"
        "export $ZEPHYR_SDK_INSTALL_DIR= ~/path_to_sdk_install_dir"
         cd to zephyr in terminal
        "source zephyr-env.sh" 

Step 4: In order to build the application use the following steps:
         
        cd to zephyr/samples/HCSR_app
        mkdir build && cd build
        cmake -DBOARD=galileo ..
        make 
 
Step 5: copy file zephyr.strip from HCSR_app/build/zephyr to our SD CARD.

Step 6: Connect the IO pins on the galieo as following:

        Connect sensors ground to galileo ground and galileo 5V to sensors VCC.
        
        Default pin values for HCSR0:

        IO2 for trigger.
        IO3 for echo. 

        Default pin values for HCSR1:
        IO10 for trigger.
        IO12 for echo. 
        

Step 7: Place SD card in galileo and boot the board.

Step 8: Shell will start to run. You will see the instructions for the app.
        
Step 9: Please make sure to select a device before starting a measurement.

Step 10: After selecting a sensor you can start taking measurements.
----------------------------------------------------------------------------------------------------------------------------------------------
Note: The following is the expected execution of the application.

First you select a device driver and then give a start command. 
The app will take the neccessary measurements and once it has 
completed you can dump/print the samples you want.

If the sensor is unable to sense or is absent the measurement will timeout.

Time out values for HCSR0 is 1 sec and for HCSR1 is 2 secs.

The app calls sensor_sample_fetch first and then channel_get for the selected device.

Print statements have been included for channel get. 

After measurement the app returns to shell without any prompt.

The driver has been initialised only for device gpio_dw. Pins: gpio (8:15) namely IO0 IO1 IO2 IO3 IO10 IO12. The sensor will
work only on this device and pins. Alter the kconfig to alter the default pin values (see step 6).


 

 
