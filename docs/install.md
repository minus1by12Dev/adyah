# Baseline ISO Installation

Make sure you have verified the download, from the previous section. 

To create bootable USB, Windows users can use [Rufus](https://rufus.akeo.ie/). Linux users can go with [Etcher](https://etcher.io/). A bootable USB is required, since Adyah boots you into a live environment.

<br/>
## <u>Adyah Standalone</u>

Most of the modern laptops now a days, come with *UEFI boot enabled*. 

Even though you can always choose the Legacy BIOS boot mode / MBR, choosing a UEFI boot mode installation has its advantages. <br/>
Read about [UEFI advantages over BIOS](https://www.quora.com/What-are-advantages-of-UEFI-over-BIOS) & For more info [UEFI Vs Legacy BIOS](https://phoenixts.com/blog/booting-uefi-mode/)

Now for a UEFI enabled system, the disk may or may not be GPT partitioned. However with a UEFI boot enabled, GPT partitioned hard disk, a EFI GRUB can be installed. <br/>
*If this does not make a lot of sense, don't fret about it. The installer will take care of these things.*

Let's get started. ( If you rather prefer a *video tutorial* [Follow this link](https://www.youtube.com/embed/pA7EF9a02eM) )

1. Plug in the Installation media and boot your system.

2. The GRUB screen shows up. Select the __Adyah [64 BIT] installer__ option and press __ENTER__.

3. You would enter the __Live Environment__. <br/>
    You can play around and try out the functionalities in the live environment, if you are still deciding whether to commit or not.
    *Not all applications are enabled in the Live Environment, but most are.*

4. Setting up Time-Zone along with Date&Time Options.
    From the desktop bar __>__ Choose System Settings Rolling Menu __>__ choose Time and Date. <br/>
    Select the appropriate Time Zone. 

5. Create Partitions.
    From the desktop bar __>__  Choose Disk Management and System Monitoring Rolling Menu __>__  choose Disk Management. <br/>
    The disk that we are working with is indicated in the top right - For our example it is __sda__.
    1. Device > Create Partition Table > In the "Select new Partition table type" > Choose GPT. Click Apply. The disk is now partitioned as GPT.
    2. Creating a SWAP partition 
        Create New Partition : Size - 4GB, Create as - Primary Partition, File System - linux-swap. Click Add
    3. Creating the Installation partition
        Create New partition - Size - 250GB, Create as - Primary Partition, File system - ext4. Click Add

    You can adjust the sizes, however just ensure that you leave at least __500MB unallocated space__ , for the EFI partition.
    <br/>Click __Apply__ to apply the Pending Operations. 

6. Double click the Installer. __ANAPMI__, the voice assisted installation program, would take over. 
   <p class="alert alert-secondary">The EFI partition does not exist yet, and so it errors out, announcing the same. __Nothing to worry about__</p>

7.  As the notification goes away, *ANAPMI offers a solution and a Terminal screen opens up.* [ Create EFI partition ]<br/>
    <i>This outlines all the disks that are GPT partitioned and prompts to choose one where the EFI partition would be created, with a default chosen.</i>
        - If you are okay with the chosen disk, Press ENTER.
        - On the "Do you want to proceed?" Y / N. Type in __Y__ and Enter.
    
    <p class="alert alert-success">And a new __EFI partition__ (sda3) is now ready. </p>

8. Let's try the installer again. <br/> ANAPMI takes over again, but this time moves beyond the EFI partition error from last time.
    <p class="alert alert-info">
        *SWAP and EFI partition have been detected, along with the Boot mode of UEFI.* <br/>
        *Date & Time have been synced.*
    </p>
    Select the Primary Disk i.e. sda [ From step 5 ], Computer Name and Installation partition [ From step 5 ].<br/>
    Provide Root password, username and user password.<br/><br/>
    Click __OK__. 

9. __Now sit back and relax.__<br/>
    With a fully automated installation, No user intervention is required. ANAPMI will take over and *will continiously notify about the progress.*
    The installation is going in the background, with the icon( show ) in the desktop bar - *Clicking on which, tells you what is happening currently.*

    ##### Milestones in the Installation Process
    - Initializing Installation Process
    - Basic set up Completed. Installing Essentials and other components
    - Extracting extras
    - Extras Installed 
    - Extracting the New Environment
    - Setting up Modern Appearance Themes
    - Modern Appearance Themes Installed
    - User Environment Claibrated 
    - Sanitizing the New Environemnt
    - Preparing User Template
    - Setting up Boot Options
    - Start up options Configured 
    - Set up is now complete.
    - Please remove the installation medium and reboot

    <p class="alert alert-info">
        The installation time could differ from across system capabilities and users, but with the very basic model, that we have used, the entire process takes about __5 mins__.
    </p>

10. Reboot.
    - The GRUB is now updated with the OS name. 
    - Select the OS. Press __Enter__.

<div class="alert alert-success successInstallation" role="alert">
    Congratulations, the set up is now complete. 
</div>

***


## <u>Adyah + Windows 10 ( Dual Boot )</u>

<p class="alert alert-warning">Assumption:  You are already running Windows on your device and want to dual boot Adyah.. </p>

Let's get started. ( If you rather prefer a *video tutorial* [Follow this link](https://www.youtube.com/embed/lFhT9_I--o0) )


1. Start the system and boot into Windows environment. *Plug in the Installation media.*<br/>
    [Access BIOS](https://www.laptopmag.com/articles/access-bios-windows-10) from Windows 10.
    <br/>
    In the BIOS options, change the Boot order to ensure that the bootable device has the top priority. [Change Boot order](http://www.boot-disk.com/boot_priority.htm)<br/>
    
    Exit the BIOS, the system should automatically __restart__. Or do a manual restart.
<br/>
  
  
2. The GRUB screen shows up. Select the __Adyah [64 BIT] installer<__ option and press __ENTER__.   
  
  
3. You would enter the __Live Environment__. <br/> 
    You can play around and try out the functionalities in the live environment, if you are still deciding whether to commit or not. *Not all applications are enabled in the Live Environment, but most are.*
<br/>
  
  
4. Setting up Time-Zone along with Date&Time Options.
    From the desktop bar __>__ Choose System Settings Rolling Menu __>__ choose Time and Date. <br/>
    Select the appropriate Time Zone. 
<br/>
  
  
5. Create Partitions.
    From the desktop bar __>__  Choose Disk Management and System Monitoring Rolling Menu __>__  choose Disk Management. <br/>
    The disk that we are working with is indicated in the top right - For our example it is __sda__.
            
    <p class="alert alert-info">
        EFI partition would already exist.<br/>
        a Microsoft reserved partition (NTFS) would also be present, where Microsoft windows is currently installed</li> 
    </p>

    *For systems, where the windows OS would have taken the entire space, __you can create / increase unallocated space.__* <br/>

    - Right Click the NTFS partition > Resize and Move
    - Change the "Free space following (MiB) field to the appropriate value - 100 GB recommended
    - Click __Resize this partition.__
    - Apply All Operations.
    
    <p class="alert alert-info">Alternatively from within Windows, you can use disk management to create a new unallocated partition.</p>
  
  
6. Adyah will need __two more partitions__
    - Creating a SWAP partition <br/>
        Create New Partition : Size - 4GB, Create as - Primary Partition, File System - linux-swap. Click Add

    - Creating the Installation partition <br/>
        Create New partition - Size - 250GB, Create as - Primary Partition, File system - ext4. Click Add
    
    Click __Apply__ to apply the Pending Operations. 
<br/>


7. Double click the Installer.
    __ANAPMI__, the voice assisted installation program would take over. 
    <p class="alert alert-info">
        *SWAP and EFI partition have been detected, along with the Boot mode of UEFI.* <br/>
        *Date & Time have been synced.*
    </p>
    Select the Primary Disk i.e. sda [ From step 5 ], Computer Name and Installation partition [ From step 5 ].<br/>
    Provide Root password, username and user password.<br/>
    Click __OK__. 
<br/>    
  

8. __Now sit back and relax.__<br/>
    With a fully automated installation, No user intervention is required. ANAPMI will take over and *will continiously notify about the progress.*
    The installation is going in the background, with the icon( show ) in the desktop bar - *Clicking on which, tells you what is happening currently.*

    ##### Milestones in the Installation Process
    - Initializing Installation Process
    - Basic set up Completed. Installing Essentials and other components
    - Extracting extras
    - Extras Installed
    - Extracting the New Environment
    - Setting up Modern Appearance Themes
    - Modern Appearance Themes Installed
    - User Environment Claibrated
    - Sanitizing the New Environemnt
    - Preparing User Template
    - Setting up Boot Options
    - Start up options Configured
    - Set up is now complete
    - Please remove the installation medium and reboot

    <p class="alert alert-info">
        The installation time could differ from across system capabilities and users, but with the very basic model, that we have used, the entire process takes about __5 mins__.
    </p>
           
9. Reboot.
    As the system comes back online, *The GRUB is now updated with the OS name.*
    
10. The GRUB now shows all options for OS selection. <br/>
    The windows boot manager on the EFI partition is visible, which if selected will get you into Windows. <br/>
    Select Adyah. Press <span class="boldWeight">Enter</span>.
    
11. Reboot. Choose windows Boot Manager and you would boot into Windows.
        

<div class="alert alert-success successInstallation" role="alert">
    Congratulations, you have now successfully installed Adyah with an existing Windows 10 OS. 
</div>

***



## Adyah + Other Linux ( Dual Boot )

Let's get started. ( If you rather prefer a *video tutorial* [Follow this link](https://www.youtube.com/embed/0XjO6eQl4WI) )


***