# Edit hosts file

The hosts file is an operating system file on a device that lets you map specific domain names to an IP address. If you want to add new entries to the hosts file, you’ll need the IP address of the server that you want to map a hostname to.

    XXX.XXX.XXX.XXX some.domain.name 

## Linux

* Open terminal application
* In the terminal, give the command `sudo nano /etc/hosts`
* Enter your administrator password after running the command
* Add as many entries as needed

## Windows

To edit the hosts file on Windows, you will need Administrator access. 

* Right-click on your text editor’s icon (for example Notepad++) and choose //Run as administrator//.
* Go to File → Open in the text editor and navigate to `C:\Windows\System32\drivers\etc\`
* From the list, click on the hosts file and choose Open
* add as many new entries as needed

## Mac

* Open the Terminal application. (Click on the Finder icon and then go to //Applications → Utilities//)
* In the terminal, give the command `sudo nano /private/etc/hosts`
* Enter your administrator password after running the command
* Add as many entries as needed
