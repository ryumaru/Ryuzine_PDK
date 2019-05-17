### Ryuzine Publishers Development Kit

The Ryuzine Publishers Development Kit (PDK) pre-packages the Ryuzine Writer authoring webapp with the Ryuzine Reader magazine webapp and Ryuzine Rack newsstand app.  It has everything you need to start authoring, previewing, and packaging your own stand-alone Ryuzine-format publications either for upload to your website or distribution as ZIP archives for offline viewing.  Your publications can be read with any modern web browser because Ryuzine is built on HTML5, Javascript, and CSS3 open web technologies.

### INSTALLATION WITH BUILT-IN SERVER (Mac or Linux)

1. Download Ryuzine_PDK and unzip it to where-ever you like.

2. Inside the “ryuzinewriter” folder there is a script named “_start” - run this script and it should start the built-in PHP web development server and automatically launch your default web browser open to Ryuzine Writer.

3. To stop the built-in PHP web server run the “_stop” script within the “ryuzinewriter” folder.

The built-in server is configured to open as “localhost” on port 8088.  This address is only accessible ON the same system running the server!  If you need to access the server over your network you will need to configure it to run on the IP address instead.  To do this:

1. Open the “_start” file in a plain text or code editor

2. Change: HOST=“localhost” to something like HOST=“192.168.1.100” (or whatever the IP is)

3. Save the file.  Run the “_stop” if you need to, then re-run “_start” and it should open using the IP address instead of “localhost.”

4. Use that IP address to access the serve from other devices on your local network. 

5. You can enable/disable various Ryuzine Writer features by editing the "writer.config.js" file in the */ryuzinewriter/js* folder.

### INSTALLATION ON DEV SERVER (All Platforms)

1. Download Ryuzine_PDK and unzip it to your Development Server (XAMPP, MAMP, or built-in Apache server on *nix systems) into the “htdocs” folder.  You can rename it however you prefer, but it will be hereafter referred to as the “Ryuzine_PDK” folder.

2. Access the “Ryuzine_PDK” folder via your development server’s URL (either localhost or IP on your LAN).  Example: http://localhost/Ryuzine_PDK/

3. You should see Ryuzine Writer (index.htm) load in your web browser.  It ships with PHP file operations enabled by default.  All your work files should be inside the “Ryuzine_PDK” folder (or requisite sub-folders for stylesheets, configuration javascripts, images, fonts, etc).

4. You can enable/disable various Ryuzine Writer features by editing the "writer.config.js" file in the */ryuzinewriter/js* folder.

You can run multiple versions of the Ryuzine PDK on the same server, so long as they are all in separate folders.

### WHITE LISTING ADDRESSES (All Platforms)

If you are not running your server on “localhost” or wish to use Ryuzine Writer on another device on your network, you’ll need to “White List” the server’s IP address, as well as the IP addresses of any devices you also want to grant access to Ryuzine Writer’s PHP File Operations.

1. Open the “functions.php” file in “ryuzinewriter/php” folder in a plain text or code editor

2. Add the IP address to the $WHITE_LIST array, along with the IP addresses of all devices on your network you want to grant access to the PHP functions.

3. Save the “functions.php” file and reload Ryuzine Writer in your web browser for the changes to take effect.

If you don’t do this, devices on your network will still be able to open Ryuzine Writer but none of the PHP File Operations will work until you white list the device(s).

### USING THE RYUZINE PDK (All Platforms)

1. Start your development server or the built-in PHP server.

2. Open the "index.htm" page inside the Ryuzine_PDK folder in your web browser (Google Chrome, Mozilla Firefox, or Apple Safari recommended).

3. A detailed user manual is available, in Ryuzine format, at: http://www.ryumaru.com/library/manual1x.htm

4. The resources for *your* publications go in the top-level folders inside "Ryuzine_PDK":
   - */css* folder: Master and Edition stylesheets.
   - */data* folder: Ryuzine Rack catalog files.
   - */fonts* folder: custom fonts used by your Ryuzine publications.
   - */images* folder: custom images used by your Ryuzine publications.
     - */subfolder* for each publication
     - */rack/catalogname/* images for each Ryuzine Rack catalog
   - */js* folder: Ryuzine Reader and Rack configuration files.
   - *rack.htm* file: Ryuzine Rack default newsstand.
   - *wip_newsample.htm* file: sample Ryuzine writer work-in-progress file.
   
5. All your publication project files will be saved with the prefix "wip_" (for work-in-progress).  Any publications you've "Built" will have whatever name you give them.

6. Configuration files made with Ryuzine Writer's "ConfigBuilder" will automatically be saved to the top-level */js* folder if PHP File Operations are enabled.

7. Ryuzine Rack catalog files created with Ryuzine Writer's "RackBuilder" will automatically be saved to the "*/data* folder if PHP File Operations are enabled.

8. The top-most */images* folder is the only place the Ryuzine Writer Editor will look for publication image files.

9. The Ryuzine Writer "Package Builder" will gather up files from the aforementioned locations and bundle them into a time-stamped ZIP archive saved into the *Ryuzine_PDK* folder. 

10. If PHP File Operations are not enabled on your development server, and for some reason you can't or don't want to enable them, you can still use Ryuzine Writer by:
   - copying the generated code out of the Export Box
   - pasting it into a plain text document
   - manually saving the document into the correct location inside the *Ryuzine_PDK* folder.
   - build packages by manually copying and pasting files into a folder and zipping it.

### CONFIGURING PACKAGING DISTRIBUTIONS

If you have enabled PHP File Operations in Ryuzine Writer (they are enabled by default) you should have the ability to “Package” Ryuzine publications you build.  On the “Export” tab select “Build Package” from the drop-down menu and a dialog will open.

Select the options you want in your package, and whether you want it to generate a folder or a ZIP archive.

By default, upon completion, Ryuzine Writer will attempt to automatically download ZIP packages to your browser’s Downloads folder.  If you would prefer it leave the generated files on the web server and offer you a link to optionally download the file from your development server edit the *“/ryuzinewriter/php/function.php_”* file on line 20 and change the one to a zero:

``php
$AUTO_DOWNLOAD = 0;
``

ZIP archived packages can be offered on your website as file downloads for offline reading.  Publications packaged into folders are ready to be uploaded to a web server for online reading.

### CODE CONTRIBUTIONS

**THIS GITHUB REPOSITORY USES SUBTREES!**  The "ryuzine" and "ryuzinewriter" folders are added as subtrees.  If you want to contribute to their development you should not work on them within this PDK repository, you should clone the corresponding repository and make changes there.  Be aware the "ryuzine" repository itself imports the "addons" and "themes" subtrees, and the "ryuzinewriter" repository imports "addons," "themes," and "xinha4ryuzine" repositories.

See also *Open Source Porject Contributions* at http://www.ryumaru.com/contributing-code/ and *Open Source Code of Conduct* at http://www.ryumaru.com/open-source-code-conduct/ for more details.

### License

“Ryuzine” and “Ryuzine Writer” are released under the Mozilla Public License (MPL) 2.0, the full text of which is bundled with the webapps. “Ryuzine Press” is released under the GNU General Public License version 3 (GPLv3).  Add-ons, Themes, Skins or other components may be under other licenses.

Distribution of publications in Ryuzine format does not require you to also provide source code if the webapp or plugin code has not been modified.

“Ryuzine” and the Ryuzine logos are trademarks of K.M. Hansen & Ryu Maru.  If you are distributing unaltered software, downloaded directly from Ryu Maru, to anyone in any way or for any purpose, no further permission is required.  Any other use of our trademarks requires prior authorization.

