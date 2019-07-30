# System SetUp and Other essential commands

## 1. Creating a User

> We don't want to be touching the existing functionality of adduser / useradd and neither did we want to customize the Add User &amp; Groups functionality; &nbsp; <br/>Hence we have our own wrapper. ( `sudo createuser` )

__There are varied ways of creating a user on the system.__

Select __Users and Groups__ and choose to __ADD__ new user.
- This would ask for the password of the current user who is logged in.
- You can provide the Name, username,&nbsp; provide a Password, and Close.

This creates a new user.

Well with the new user created, <em>let's switch to the new user</em>.<br />
Power Options <strong>-&gt;</strong> Switch User <strong>-&gt;</strong> Choose the new user (<span style="font-size: 8pt;">created earlier, from the dropdown</span>) <strong>-&gt;</strong> Enter Password <strong>-&gt;</strong> Login.</p>
    
<div><span style="font-family: 'trebuchet ms', geneva, sans-serif;">Oops.. what just happened!! The look and feel have changed completely. The entire user interface now looks like Debian and t</span>he complete customization, that ships on top of Debian to give the feel of Adyah is gone.</div>
<div><em><span style="text-decoration: underline;">The templating system does not kick into effect if you use the
        default user Management tools</span></em></div>

<br/>
<span style="font-size: 16pt;">Now</span>, even though this feels like a bug, but this is something that has been well thought of and incorporated into the system.&nbsp; The kind of templating that Adyah uses, for the customized look and feel is pretty heavy.&nbsp; A lot of software would be required to create users themselves ( in an automated
way ). <br />
If each of these users were to get the Adyah template,&nbsp; the home folder for such users would have an additional 100-500 MB, based on the application chosen.&nbsp; But this would be unnecessarily taking up space since these users are for functionality only.

<em>Hence normal default user creation, that happens via <strong>useradd</strong> / <strong>adduser</strong> (Terminal ) should continue the same way, they happen in Linux today.</em>

<span style="font-size: 13pt;">So we should have an explicit way, using which if i create a user, the user should have a Adyah look and feel.</span>

Switch back to the previous user. and from within a Terminal window &nbsp; `sudo createuser.`

1. <em>Create New User y/N</em> =&gt; Y
2. <em>Enter UserName</em>
3. <em>New Unix Password</em>
4. <em>Enter Full name</em>. Let everything else be default. Press ENTER.
5. <em>Enable AutoLogin y/n</em> =&gt; n. If selected Yes, by default this user will be selected.

<p><strong>DONE</strong></p>
<p>Now if we switch User, and login with this new user - You would see the familiar Adyah look and feel.</p>


***

## 2. Kernel Update
    
Everything happens behind the scene and we are not involved manually.

__For Checking.__<br/>
First check the Kernel version, uname -a. This shows what kernel version was shipped with.
    
__Updating__<br/>
Terminal : __kernel-update__
Update Kernel ( Icon )

There is a file created in /opt, that holds the system. while the kernel update is going on. As long as this file is there, any other updates will not run. Also will not be able to restart. ANAPMI will not let you proceed. Go and delete this file, if you are stuck.

System Restart Required [ __Better Save the work before proceeding__ ]. Execute. 

The kernel would be updated and then the system restarts, because we will be needing to rebuild the kernel modules for Virtual Box and Vmware ( which are part of the OS ) and also updating the GRUB.

Sit Back and Relax. ANAPMI will take over, Connect over the Internet, download Kernel, Modules and Headers, Install and Reboot.
    
- Updating Kernel to the latest version
- Installing Modules and headers
- Restarting the System
- In the GRUB, the new Kernel is now available. ( Select the OS with the new Kernel )
- As the system reboots, the process automatically picks up from where it left
- Removing the old kernel
- Configuring VMware Modules
- Configuring VirtualBox Modules
- Updating GRUB
- Kernel Updated Successfully

Check again
- System Information [ Icon ] to find more info about Kernel.
- Terminal uname -a
- Unsynced Software
  
***

## 3. Find fastest and nearest APT repo

To understand the concept of repository Click here

__etc/apt/source.list__ is the file that holds the latest Debian Repository.

How do you set up the repositories?
I might try to find out some package and would be presented with a list of mirrors, across the world from where i can download the package, *but what if i want my system to be plugged into one of those mirrors.*

Also sometime that mirror might not itself be working.

<p class="alert alert-info">
So what we thought was why not have something, which can automatically detect which mirror would be the nearest to me and then set up the whole environment, so that mirror is connected, when i start writing the apt-get install and for that we have a simple command.
</p>

__setupapt__

- Automated Mirrors - Find all Mirrors; Go through the list and find the best.
- Also runs apt-get update to make your system completely enabled.

__Recommendation__ Before installing anything on Adyah; <u>*run setupapt first*</u>. 
This will ensure that you are connected to the nearest mirror and then run your apt-get install. <br/>
This increases efficiency, so that whenever you are installing anything, you will always be connected to the nearest / fastest mirror.

<p class="alert alert-info">
    Also modified the apt-get process in Adyah; so you don't get just the normal apt-get installation; but a parallel apt-get based out of ARIA-2 internally. *Things just run faster.*
</p>

Check the source file now. The mirror would have changed. Scroll to Debian SID

***


## 4. System Vitals Set up
Implementation over conky, which provides desktop visualization effects.

Select System Vitals. The conky bar that comes up shows

- Date & Time Information
- Various CPU parameters
- Running Processes
- Distro Name/ Kernel info *and*
- Rest of the things

*What you might want to add is "Weather Information"*. A weather center is already bundled along.

1. Accessories __>__ Weather Indicator

2. Shows an Icon on the Desktop Bar __>__ Change properties __>__ Set up as per your location
    *But if you want it to be integrated in the conky bar*, then we are right now using the weather API channel and it requires a GUID and a registration.

3. Open Terminal __>__ conkysetup

4. It will show you the network Info [ Starting with ens is ethernet NIC, starting with WL is wireless card.
    Also show the Current User Info.

5. Go to the URL and find your city, and the corresponding city code. Create an account and you will get an API key.

6. Go back to the Terminal
    - Enter the City code
    - Enter the API Key
    - Network Information

Confirm changes Y/N => Y. Cntrl + C on the terminal to exit.

From within the Home Folder. Remove *weather.json* and *weather2.json*

Now when you begin conky, the weather elements would also be visible and now the temperature is visible.

***


## 5. Understanding your Desktop

One aspect that we __really focussed__ this time aorund, when we were *building the distribution from scratch*, is how a modern user is applying himself on the desktop environment nowadays. <br/>
You can choose any desktop environment, Gnome, Xfce, Wayland, but essentially the modern user has been now modelled in a way in which he has to approach the desktop.

The crux of that way is that, because we are now using so many categories of applications, 

1. So we choose a category first today. 
    You want to communicate first and then under communication you will have a lot of choices. 
    Similarily you just want to go to the net and you could have n number of choices based on what are you trying to do.

2. So essentially this ergonomics, __Applied Ergonomics__, is now the base of the Adyah environment. 
    If you look at this desktop, it clearly focusses a lot on this aspect 
    
As you can see we have __22__ different categories and each of these categories is *one of the essential elements of your day to day use of the system*.

So first you need to choose the category, and then under the category you will have these options which you can click and you can see more options under that section.

- Say suppose Text editor - *It means i am writing something.*
- Similarily under the Internet Options - *you have all the browsers, email, download managers.*
    
And the menus are all rolling menus. 
So you can click on any menu - Right Click __>__ Panel __>__ Panel Preferences and you can just roll down the application - up and down ( Whichever is moved to the top, is the preferred application. ), such that it is reflected here, because of which *you could have 22-25 applications that you are using, right in front of your screen*. 

So within a few minutes, the complete environment can change and this is remarkable, you can a completely new environment ready in front of you with just a few clicks.

- Under any of them you can add new items. This will create new launchers.
- And if we choose this option, you can search any other application , that you are looking for and add them and can then reconfigure.

<br/>
### Wallpapers
Right Click __>__ Properties __>__ Wallpapers __>__ 50+ wallpapers.

<br/>
### Themes
Adyah ships will the best collection of modern themes. So you can go the themes section __>__ Appearance __>__ and choose any theme. Shipping with 6 themes and Icon sets.


***

## 6. Anapmi - Voice assistance program


***

  
## 7. PrathamOS Update

*Through `prathamos-update` command you can easily upgrade your system.*

Whenever your system boots up, and if you are connected to the interent, the system will try to connect the repositories and will try to find out if any updates are available and 

- You will see an icon which will be telling you about the current update status *and*
- Will also be showing what update is available and based on that you can proceed.</p>

Run "Update PrathamOS" ( from search Icon ) and this will ensure that ANAPMI takes over. __OR__ <br/>
From the terminal `prathamos-update` the entire process will run in the terminal, with complete logging.

<p>Completely Automated Process. </p>

1. Update notification comes up.
    `/etc/apt/ver` file holds the current version of the system. This is the file that the system checks and decides whether the system needs to be updated.

2. Click the update icon

3. Browser window opens up - outlining the new update and its details.
    The "Unsynced software" is the area where prathamos-update takes the most effect. ( to know what version of aoftware are you using )

4. Custom Commands - shows all the custom commands that are available.
    <p class="alert alert-info">We recommend setting the volume to > 50% for the notifications to be audible.</p>

5. Download the updates. `/opt/UnsyncedUpdate` folder along with `POSUPDATE file` that will keep the system locked during the update.
    Unsycned software are being updated. Please wait for completion.
    Unsynced Software Updates Successfully.

6. Now the icon disappears, and also the folder and file are gone.

7. You can check the *Unsynced software page*, and you would see the updated versions.


***

## 8. Installing a Software - managed & unmanaged

***


## 9. Local Network File Sharing

***


## 10. PrathamOS download Manager

*Only for Linux Users.*

The OS, has been built around a lot of components, which need to be updated regularly. The softwares are distributed on multiple mirrors across the globe. These mirrors could be down, and while you are downloading these files, the connection might just go off.
*Now if you are downloading via the browser, then all is lost.*

Also you cannot pause the download in between, and resume later on.

The __PrathamOS download manager__ is based on the __Torrent model__ i.e. a large file is divided into a lot of chunks. and these chunks are downloaded.

- This model allows us to create a failover ( continuous retrying model for timed out chunks, pause and resume ) , which is very helpful if you are on a global open sourced mirror, where things can just go down and you might need to resume later.
- Chunks of 50 MB. So 1GB file would be broken into chunks of 50 MB and then downloaded.
- Getting large files becomes very easy.

`prathamos-get` 

*Behind the scenes*, all the updates and install use the PrathamOS download manager.

1. <u>From within the PrathamOS environment</u>, can be used manually to get the Vmware / VirtualBox image.
    `prathamos-get` Choose one of the three options (1 - baseline, 2 - Vmware, 3 - VirtualBox) . No need to go to the site and download.
    Press __Enter__
    *Where ever you run this command from, is where the download happens.* So ideally navigate to the folder __>__ and Right click __>__ Open the terminal and then run the command.</p>

    - GetPOS.sh will be created here.
    - Also there is a file that keeps track of the progress. So while you need to resume, run this file. ./......... .sh
    - The folder will have a lot of chunks. Also the Download Manager does a parallel download, resulting in very very fast download. [ *behind the scene uses Axel* ]
    - __Ctrl+C__ to stop the process. And on resuming, the downlaod will restart from the lost chunk.

    On completion, all these chunks would be collated into one single piece of software.

2. For other Linux distros, need to install Axel, and then the specific command. <br/>
`rm -f GetPrathamOS.............`


***
<br/>
