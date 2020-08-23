# User Interface
By default bimU.io Viewer API renders a 3D canvas without loading any user interface. The ```showUI``` option in the viewer configuration object has to be explicitly set to ```true``` to enable the default toolbar. The [Materialize](https://materializecss.com/) framework is used under the hood to help developers quickly put together user interface. You can leverage its existing UI components and functionality if necessary. In case of CSS conflict, the ```showUI``` option should be set to ```false```. Then the Materialize framework won't be loaded at all. Ideally, you should overlay your own UI on the viewer component and get it integrated with a UI framework within your production tech stack. 

### Default Toolbar
The default toolbar contains a few icon buttons that are identical to the ones on bimU.io Viewer, including navigation controls, element information, measurements, full screen, etc. Each default button has a predefined and fixed DOM element ID. The ```buttonColor``` option in the viewer configuration object can be changed to suit your desired color scheme.

### Custom Button
You can also add more buttons to the default toolbar. The ```addCustomButton``` function allows to customise an icon button with various styling options. Courtesy of Google, the [Material Design Icons](https://material.io/resources/icons/?style=baseline) can be of use here. To remove an existing (either default or custom) button, simply call the helper function ```removeDomElement```. A couple of examples below.

``` javascript
viewer.addCustomButton("button1", "wifi", "#2196F3", "Like it", function(){ alert("You liked this model."); });
viewer.addCustomButton("button2", "router", "#4CAF50 ", "Unlike it", function(){ alert("You unliked this model."); });
```

### Dialog
If you need to pop up some instruction or information for your users, the ```showDialog``` and the ```closeDialog``` functions come in quite handy. The ```showHelp``` and the ```showElementInformation``` functions use it internally. An illustrative example below.

``` javascript
let now = new Date();
let html = `
<table>
    <tbody>
        <tr>
            <td><strong>Timestamp</strong></td>
            <td>${now}</td>
        </tr>
    </tbody>
</table>`;
viewer.showDialog("Do you want to submit your request now?", html, "No", "Yes", () => { 
    // Do your stuff...
});
```

### Background
The viewer canvas comes with a white background by default. Call the ```setBackgroundColor``` function to select a desired color.
