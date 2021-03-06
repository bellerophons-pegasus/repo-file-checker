# repo_file_checker 

# Updated: 19. July. 2017

### The Repo File Checker functions:

  - Creates a Reports in a HTML format.
	* File and Directory List
	* Error List
	* File Type List
  - clamav extension for the file virus checks.
  - PHP progressBAR (https://github.com/guiguiboy/PHP-CLI-Progress-Bar)
  - BagIT PHP checker (https://github.com/scholarslab/BagItPHP)
  - Compare the MIME type and the extension
  - Password protected ZIP files checking. The script is trying to extract the zip files.
  - File name validation (contains spaces or special characters)
  - File name duplication checking
  - Password protected xlsx and docx checking based on the MIME type.
  - Password protected PDF checking based on the PdfParser library (https://github.com/smalot/pdfparser). The script can check the PDF's from version 1.5.
  
  
### System requirements:  
  - PHP 7
  - oPCache or similar
  - PEAR
  - PEAR Archive_TAR (https://pear.php.net/package/Archive_Tar/download)
  
  
### Using:
  - install composer components
  - rename the config.ini.sample to config.ini
  - add a temp Directory and a report directory location to the config.ini file.
  - call the index.php file from the CLI, you have two arguments, first is the directory what you want to check, the second is a checking option: 0 => check files / 1 => check files and viruses.
	For example: -> "php -f .\index.php c:\mydata\ 0"
  - if You have bagit files, then please place them into a folder called "bagit" and also please compress your files into a tgz file.

  
### Test Files:
You can find the testFiles in the _testFiles folder. We have test for the following cases:
  - duplicates -> duplicated files
  - goodFiles -> every file is okay, html report will be generating
  - pwProtected -> there is a password protected zip file in the folder.
  - wrongContent -> here We removed the PDF text from the PDF file source. And we renamed the gif file to png.
  - wrongFilename -> the filename contains not legal characters
  - wrongMIME -> wrong MIME types

  If you have big size files, then please allow oPCache in your php settings.
  
  If you want to use your own big files for testing, then you can mount your own directory to the VM /home/vagrant/testfiles/ directory, for this you need to do the following steps.

    - Start the VM and press right click on your VM, select Settings from the menu
    - Now select Shared Folders
    - Click on the Transient Folders line and then click on the Folder with a green plus sign icon on the right side of the window.
    - Browse your test files folder in the Folder Path option, below the Folder Name will be the name what we will use inside the VM to mount this directory.
    - Login to the VM and run the following command: mount -t vboxsf the_share_name /a_folder_name (in our example: mount -t vboxsf testfiles /home/vagrant/testfiles/)
Here you can find an image about the steps:
https://user-images.githubusercontent.com/20183307/28311284-72ba849a-6baf-11e7-9b93-f06e89cb12c4.png
  
# Updates:

#### 19.07.2017
- BlackList added

#### 18.07.2017
- New PDF checking library
- phpMussel removed
- The script is now using the server clamav virus extension

#### 06.07.2017
- Reports are now in searchable tables (Jquery Datatable)
- Some improvements in the code
- PDF library changed, because the previos one had some problems
- New arguments in the run command, because the phpMussel is very slow in big data sets.

#### 04.07.2017
- Error Report css changes
- Lower/uppercase extension problems fixed in the reports.
- Reports filesize section changed, the script is checking the filesize and it will format the value based on the size.
- Duplicate report now contains the duplicated files folders too.
- Filetype list ordered by Alphabetically


#### 30.06.2017
- Password protected PDF file checking.

#### 27.06.2017
- Composer added to the project
- bagIT file checker implemented.


#### 23.06.2017
- Directory list extended with the root directory info, Directory Depth and Directory files sum size.
- File Type List formatting changes
- Password protected docx checkings


#### 22.06.2017
- ProgressBar added
- Xlsx pwd file checker
- Reports template generation changed
- New report: list by extension, size, count, sumsize, min/max size, avgsize.
- File list report has now 2 sections: Files/Directories.

