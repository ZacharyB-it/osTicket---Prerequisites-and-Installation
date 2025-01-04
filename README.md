<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Windows 10 virtual machine
- Access to Internet
- [Files you will need](https://drive.usercontent.google.com/download?id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD&export=download&authuser=0)
- Item 4
- Item 5

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into your virtual machine with remote desktop. After doing so download the files above and extract or unzip the files(right clicking the folder as shown in the photo above). 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install / Enable IIS in Windows WITH CGI by going into "Control Panel", then "Programs", then click "Turn Windows features on or off". When you do that you will see the image above select the box next "Internet Information Services" make sure it is marked. After this hit the plus button next to "World Wide Web Services", then the plus button next to "Application Development Features". Doing this should allow you to see "CGI" in the image above. Check the box next to "CGI". Hit ok and let Windows download and apply those files.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to the file we extracted earlier and install the PHPManagerForIIS_V1.5.0 and rewrite_amd64_en-us files. Follow the download instructions provided by the programs.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next create a folder in your C: drive called PHP. Your C:Drive is found under "This PC" and will be called "Windows(C:)".
  Now, Extract/unzip php-7.3.8-nts-Win32-VC15-x86.zip from the file we installed into the "PHP" folder we just made.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now install VC_redist.x86.exe from our "osTicket-Installation-Files". After doing that install mysql-5.5.62-win32.msi.
  While you are installing MySQL when it get to the above image choose Typical. Then keep the box next to "Launch the MYSQLInstance Configuration Wizard" checked. It will then launch you into the configuration wizard.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Configuring the MySQL Server. Choose "Standard Configuration". Then hit next after the following page you don't have to change anything hit next again. Now choose your password. MAKE SURE YOU REMEMBER THIS!!! When you type your password hit "Next" then "execute" and finally "Finish".
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now Open IIS as an Admin, type IIS in the search bar, right click it and choose run as an adminstator. As shown in the image above.
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we will registering PHP. Click "PHP Manager". Proceed to click Register new PHP version. Now copy and paste" C:\PHP\php-cgi.exe "into the box asking for a path. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ok now we have to stop and start IIS so we right click whatever you have named your Virtual machine and hit stop wait a few moments. Then right click the name again and hit start. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we go back to the “osTicket-Installation-Files” folder, unzip/extract “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”. After doing that RENAME the "upload" folder to "osTicket". You can rename by right clicking the upload folder and choosing "Rename".
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ok now we have to stop and start IIS again. After doing that look on the left side of the window click the arrow next to your VM's name, then the arrow next to "Sites" then the arrow next to "Default Web Site". You should be able to see osTicket click on that. On the right side of the screen click browse 80.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now some extension are not currently enable you can enable them by going into PHP manager for osTicket. Double click on PHP Manager and then scroll down to PHP Extensions and enable these three "php_imap.dll", "php_intl.dll", "php_opcache.dll". To enable them right click on them and hit "Enable". Now refresh the Osticket website. Some extension should be enabled now
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we have to rename "ost-sampleconfig.php" to "ost-config.php".now we navigate to "C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php" in our file system. Locate "ost-sampleconfig.php" and now rename it to "ost-config.php".
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After the above steps are complete right click "ost-config.php" again and click properties g
o to "Security" then click "Advanced". Should look similar to image above now. Click "Disable inheritance" then "Remove all inherited permissions from this object" then click add and choose the people you want to have permissions for this. Then check Full control and hit Ok, Apply, Ok, Ok.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now go back to the osTicket installer webpage. Hit continue and fill out the forum until you get to the database settings.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Now we go back "osTicket-Installation-Files” folder and install HeidiSQL and launch it. Hit new in the bottom left corner. Now remember your password and username for Root/MySQL you set up earlier put those into the user and password here. Then click open.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Right click the dolphin with unamed next to it and create a new data base called "osTicket".

  After doing that go back to the form you were filling out complete that info and hit install now and it should be installed.
</p>
<br />
