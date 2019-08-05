# Upload a BIM Model

There are two ways of uploading your BIM models:

- **Upload from BIM Software:** Uploading from a BIM model view within authoring software gives you more control of how it looks like on bimU.io. What You See Is What You Get (WYSIWYG). Please follow the instructions in the next section to install the bimU.io Launcher before uploading a BIM model from authoring software.
- **Upload IFC files:** The industry standard IFC (Industry Foundation Classes) format is also supported. Most authoring software can export to an IFC file. You can then upload it to bimU.io directly. 

## Install bimU.io Launcher

**_Note that you must have bimU.io Launcher installed to upload models from BIM software._**

### What is bimU.io Launcher?

bimU.io Launcher is a middleware that exchanges data between bimU.io and BIM software. It is a background process running along with BIM software without a user interface. Unlike other third-party tools that require a plugin opened manually within various BIM software for exporting data, bimU.io Launcher implements the so-called **Pluginless** technology which allows users to stick with a single user interface, i.e., using bimU.io via browser.

### Supported BIM Software

- Autodesk Revit 2014-2020
- Autodesk Navisworks 2014-2020
- Trimble Tekla Structures 21.0-2019

### Download Installer

**_<a href="#" target="_blank">Download bimU.io Launcher 2019.x.x.0</a>_**

The latest version of bimU.io Launcher is 2019.x.x.0. The installer can downloaded from the link above. **__Please close all BIM software sessions prior to installation.__** Technically speaking, admin right is NOT required for the installation. Please speak to your IT staffs if you don't have permission to install it.

### Automatic Update

bimU.io Launcher performs automatic update behind the scene for the installed components. However, you will need to download a new installer for a new version of BIM software. For example, bimU.io Launcher can update itself for Autodesk software 2014-2020 whenever bimU.io has a new release or a bug fixed. But a new installer will be required to support Autodesk software 2021 next year.

![Screenshot](images/placeholder.jpg){: class="center" style="width:300px"}

You can check out the installed version fo bimU.io Launcher from the top menu bar. For an automatic update to take effect immediately, we suggest repeat the following steps **twice**: 

1. Restart your machine or log off Windows.

2. Make sure you have a stable internet connection.

3. Open any supported BIM software.

4. Open any file and wait for one minute.

### Troubleshooting

If you have any problem installing or using bimU.io Launcher, please log a support ticket with the following two items attached if they exist:

- **Log File:** Open Windows File Explorer and paste **%localappdata%\temp\bimU.io.log** in the address bar. The log file is stored as **launcher.log** in the folder.
- **Error Code:** An error code would be shown in browser When something goes wrong on bimU.io.

## Upload from BIM Software

![Screenshot](images/placeholder.jpg){: class="center" style="width:300px"}

Uploading from various BIM software has similar steps on bimU.io:

1. Open a 3D model view in any supported BIM software.

2. Make sure visisblity and appearance of model elements are as desired.

3. Click the plus button in the top menu bar and select **Upload from BIM Software**.

4. Select a **Model Source** (i.e., BIM software) where you want to upload from.

5. Review screenshot and click the **Refresh** icon button if you want to start over.

6. Change **Model Name** if you want a different one from current filename.

7. Click the **Upload** button to proceed.

Every BIM software handles 3D computer graphics differently. The general rules for bimU.io export are:

- Only visible model elements in the current 3D view are exported.
- Model unit is converted to meter.
- Materials are exported without textures.

See below for more details around how bimU.io exports a model from every BIM software. 

### Export from Autodesk Revit

_2D View_ and _Family Document_ are NOT supported for export at the moment. You must have a _3D View_ opened to start the upload process. Visible _Linked Models_ in the current _3D View_ are exported, too.

Visisblity and appearance of _Elements_ can be determined based on a number of factors, such as _Section Box_, _Visibility/Graphic Override_, _Temporary Hide/Isolate_, etc.

Both _Type Parameters_ and _Instance Parameters_ are exported. Some file metadata, such as _Document_ properties, _Project Information_, _Project Position_, _Site Location_, etc. are exported, too. Model coordinates are converted to _Shared Coordinates_.

### Export from Autodesk Navisworks

Appearance of _Model Items_ can be determined by _Color and Transparency Override_. However, _Sectioning_ is NOT currently supported. If you don't want to export some of the _Model Items_, you'll have to select and hide them manually.

Most of the _Properties_ shown in the _Properties Window_ are exported, including _Document_-level properties.

### Export from Trimble Tekla Structures

Visible _Model Objects_ in the active _Work Area_ are exported. Color settings are defined by Tekla and cannot be changed.

The exported _Model Objects_ include _Part_, _Assembly_, _Pour Object_, _Base Component_.

The exported properties include _Model Information_, _Project Information_, _User-Defined Attributes_, and the properties defined in the _Global Attributes_.

### Export from Other BIM Software

bimU.io Launcher doesn't integrate with other BIM software at the moment. As a workaround, you can export to an IFC file from most BIM authoring software, such as Graphisoft ArchiCAD, Bentley OpeningBuildings Designer (formerly AECOsim Building Designer), etc.

### Monitor Progress

![Screenshot](images/placeholder.jpg){: class="center" style="width:300px"}

You can check out the progress from the top menu bar while a model is being exported and uploaded. **DO NOT close the browser window before the upload is finished.** You might cancel it if necessary.

## Upload an IFC File

Both IFC 2x3 and IFC 4 formats are supported. Uploading an IFC file is quite straightforward. Simply click the plus button in the top menu bar and select **Upload IFC File**. The upload process will start as soon as you select or drag and drop an IFC file in the dialog.

## Upload Other 3D File Formats

We aim to support more and more authoring software and 3D file formats in the future. The below items have been prioritised for developement. Note that the delivery timelines may change. Stay tuned on our our social media (<a href="#" target="_blank">Twitter</a>, <a href="#" target="_blank">Facebook</a>, <a href="#" target="_blank">YouTube</a>, <a href="#" target="_blank">Blog</a>) for the updates.

- **McNeel Rhinoceros 3D (.3dm):** January 2020
- **Trimble SketchUp (.skp):** March 2020

## Notifications

bimU.io will process your model immediately after upload. Depending on file size, it can often be done in minutes. When a model is ready to view, you will receive an email notification and also a browser notification if you have bimU.io opened.

## Current Limitations

To optimise computing and storage resources, bimU.io limits the size of a model that you can upload to **bimU.io Viewer Free**. Currently, the following soft limits apply per model file and will be increased for paid users in the near future.

- **Compressed upload file size:** 100 MB
- **Number of visible model elements:** 100,000
- **Uncompressed model geometry size:** 400 MB