-- Instructions -- 

1. Extract the .zip in to your home folder, (the one with your username where you find the folders Documents,Downloads,Pictures, etc.)

    you should now have a folder named "Elegant" in your home folder.



-- In Terminal --

2. Check if Plymouth is installed, if /usr/share/plymouth/themes exists. if you are running linux mint it should be installed by default. Otherwise Install Plymouth themes :

    sudo apt install plymouth-themes


3. In terminal type the following command

    sudo cp -r ~/Elegant /usr/share/plymouth/themes/Elegant

this copies the Elegant theme folder into the plymouth themes folder.


4. Install the theme by creating a symbolic linking from your new theme to the default.python file, be sure to replace the template variables used:


    sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/Elegant/Elegant.plymouth 100


5. Select the default theme.
   
    sudo update-alternatives --config default.plymouth

You should now see, a list of themes type the number corresponding to your theme.

you could also in the prior step adjust the priority in the command to above (100) or larger than the than the highest value in the theme list. 


6. Update the initramfs image.

    sudo update-initramfs -u


7. Modify Grub.


    sudo nano /etc/default/grub



        Find the line: "GRUB_CMDLINE_LINUX_DEFAULT". Make sure its : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

        then,

        find the line: "GRUB_GFXMODE" = change it to at least: 1920x1080 (this is the size of the images)

        Ctrl- o to save 

        Ctrl- x to exit nano

8. Update grub

    sudo update-grub

9. Check and see if it works as intended

    sudo plymouthd ; sudo plymouth --show-splash ; sleep 10 ; sudo killall plymouthd



5. Now reboot.

And enjoy.

This theme is a modification of a theme from ToddServo, https://github.com/ToddServo/Plymouth-Animated-Boot-Screen-Creator
I simplified a few steps. if you for any reason is unable to get it to work with my instructions, ToddServo has troubleshooting steps in his guide.

