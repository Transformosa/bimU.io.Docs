# Manage BIM Models
After logging in successfully, you should see the main user interface which is made up of three sections and looks something like the following screenshot.

![Screenshot](../images/mainui.png){: class="center" style="width:100%"}

- **Menu bar** is on the top right where you can upload models, check out notifications and upload progress, edit user profile, check launcher and web app versions, report problems, view documentation, etc.
- **Onboarding Information** provides some basic guidance on how to use bimU.io.
- **List of Models** is a table of all uploaded models. Your models should be managed from here. See more details below.

### Sample Models

Four sample models are provided for a new user to play around: 

- **Sample_Building.rvt:** A 6-floor residential building modelled in Autodesk Revit.
- **Sample_Federated.nwd:** A number of structural, Mechanical, Eletrical, and Plumbing (MEP) models combined in Autodesk Navisworks.
- **Sample_Tekla:** A steel structure modelled in Trimble Tekla Structures.
- **Sample_Bentley.ifc:** A simple building frame modelled in Bentley OpeningBuildings Designer (formerly AECOsim Building Designer).

### Model Properties

- **Name:** Model filename or document name.
- **Label:** Indicating whether a model is labelled.
- **Source:** Indicating what BIM software or format a model was uploaded from.
- **Size:** Model file size after compression. IFC files won't be compressed.
- **Updated:** Last updated timestamp. Models are sorted by this property.
- **Share:** Indicating whether a model is shared.

### Label a Model

Label is a simple way to categorise your models. There are five different color labels to choose from. Click on the same color label to remove it.

### View a Model

Open model viewer by clicking the magnifier button or simply clicking on a model name.

### Share a Model

A **Share Settings** dialog will pop up after switching on the toggle button. You can also open it from the three-dot menu. 

![Screenshot](../images/share_settings_new.png){: class="center" style="width:80%"}

Once sharing is enabled, a model is accessible by anyone who has the link shown in the dialog. Login is not required to view a shared model. It is not possible to make any change to it via the link. But we strongly suggest set a password to protect your model and only share it privately. To disable sharing, simply switch off the toggle button.

![Screenshot](../images/password_protected_screen.png){: class="center" style="width:80%"}

Recently a basic comment functionality has been added to bimU.io Viewer that allows guest users to create markups or comment on markups within a password-protected BIM model without creating an account. When a password is set, guest users will then be asked to provide their name in addition to the password on the login screen. The name will be used for comments in the current session.

### Embed a Model

You can embed a model and view it within other web applications, such as Microsoft Teams or Microsoft SharePoint. More details can be found [here](embed-in-other-applications.md).

### Rename a Model

To rename a model, click the three-dot button and then click the **Rename** option from the context menu.

### Delete a Model

To delete a model, click the three-dot button and then click the **Delete** option from the context menu. Note that this operation cannot be undone.