# Edit exif metadata in images

## Windows

* Click right then properties on the Image file
* Click on the Details
* In this tab, at the bottom left, click on "Delete properties and personal information"
* Select Create a copy with all possible properties removed or you can also select Remove the following properties from this file, and select the properties you want to remove.
* In Origin, you can edit the Author, Data taken, Date acquired, and Copyright.

For more on metadata on windows:

* The Details tab divides metadata properties in a number of sections, different for each file type. The image file is divided in six sections. The first section is called Description, and you can click the value field for Title, Subject, Tabs, Comments, and edit its information. 
    * Image shows relevant information about the image, all of which is automatically added an cannot be modified.
    * The Camera section includes the details of the camera that was used to take the picture. Some of these fields can be modified.
    * The Advanced photo section shows fields useful for photographers. Only some of the fields can be edited.
    * File shows file name and type, location path, date created and modified, owner, and computer name where the file resides. These fields can not be edited.

### IrfanView

This may become complicated if needing to remove EXIF ​​data on multiple images from a complete folder. 

[IrfanView](https://www.irfanview.com/) is a free image viewer software and photos that also gives the possibility to remove all data from an image or photo file. When saving an image, an option "Keep Original EXIF ​​data" is present. Unchecking the option removes all EXIF ​​data from the image file. Can be done in bulk. From the File> Batch Conversion / rename menu, data on several image files can be deleted in one click. 

## Mac

* Open Photos app on your Mac. 
* With Photos tab selected in the left pane, rght click any thumbnail on the right and select Get Info. A window opens, showing the file name and format, camera data, and profile photos of people that Photos recognizes.
* Click in the window, and you can add or edit title, description, keywords and location. 

For more data:

* Open image in Finder.
* Click Tools > Show Inspector in the top toolbar. This opens a window containing four tabs. The first tab provides summary information, and clicking on the second tab reveals 5 more tabs: General, IPTC, EXIF, JFIF and TIFF. Click on these to see all the metadata information.

### ExifEdit

[ExifEdit](https://www.exifedit.com/for-mac/) gives an intuitive way to edit EXIF & IPTC metadata for thousands of photos in a single click.

## Linux

### ExifTool

ExifTool is a perl program that can be used to read and edit exif metadata in images. It is available for Windows, MacOS and *nix systems.

    $ exiftool imagename.jpg 

To remove, for example GPS data (not found in the above image file, but if you have it in yours) - replace image.jpg with your image file:

    $ exiftool -gps:all= -xmp:geotag= image.jpg

### imagemagick

The mogrify command of imagemagick can be used to strip Exif data from images. For the same file as above and then checked with exiftool again:

```
$ mogrify -strip imagename.jpg
$ exiftool imagename.jpg
```

For removing Exif data from all jpg images in a directory and all of its sub-directories recursively:

    $ find ./path/directory -type f -iname '*.jpg' | xargs mogrify -strip

### exiv2

The exiv2 tool also has a command for deleting all Exif data from an image:

    $ exiv2 rm imagename.jpg

For removing Exif data from all jpg images in the current directory:

    $ exiv2 rm *.jpg

For removing Exif data from all jpg images in a directory and all of its subdirectories recursively:

    $ find ./path/directory -type f -iname '*.jpg' | xargs exiv2 rm


