# Getting Started with bimU.io Viewer API

Advanced users, digital specialists, and software developers can take advantage of bimU.io Viewer API (Application Programming Interface) to create bespoke BIM Web applications based on the bimU.io platform technology. We aim to make your development experience simple and allow you to quickly put togehter BIM applications on the Web without having to handle 3D computer graphics from scratch.

### Overview
bimU.io Viewer API
Extend bimU.io Viewer's core functionality
Create BIM-based digital solutions , such as custom visualisation, data analytics, Digital Twin, IoT (Internet of Things), etc.
Out-of-the-box 3D BIM viewer and database. 

### Prerequisites
- Programming knowledge
- bimU.io Pro account
- bimU.io model
- Website hosting

### Main Concepts
Same functionality on bimU.io Viewer. Customise how viewer or your model looks like.
Render viewer on your own webpage. Interact with viewer component with JavaScript API.
Viewer component is pure front-end. Browser-side.
Authentication requires back-end. Server side.
Viewer loads model geometry.
BIM database query.

### Quick Start
Minimum setup
jsfiddle + dependencies

``` html
<div id="viewer" style="width:1000px;height:500px;background-color: black;border: 5px solid black;"></div>
```

``` javascript
let onPorgress = (e) => console.log(e);
let onLoaded = (e) => console.log(e);
let onError = (e) => console.log(e);

let viewerConfigs = {
    domElementId: "viewer",
    showUI: true
};
let viewer = new bimU.Viewer(viewerConfigs);
viewer.initialize();

let modelConfigs = {
    modelId: "5e545747597b680004e70414",
    password: ""
};
viewer.loadModel(modelConfigs, onPorgress, onLoaded, onError);
```

### Support
Please log a ticket on bimU.io's support centre or email support@bimu.io if you have any query. bimU.io Support Team is more than happy to answer any technical questions.