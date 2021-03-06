# Initialisation
Before initialising the viewer component, please make sure all dependencies are installed and imported properly. You might see an error message in browser console if an imported Three.js version is incompatible with the current bimU.io Viewer API version.

### bimU Namespace
If bimU.io Viewer API is imported successfully (either via ```<script>``` tag or ES6 module), all available classes, enums, utilities, etc. are exposed under the bimU namespace. You can use dot key to explore the bimU variable. Some examples below.

``` javascript
// Initialise a viewer
let viewer = new bimU.Viewer(viewerConfigs);
// Initialise a property selector
let propertySelector = new bimU.PropertySelector("Text", "Mark");
// Enum
let func = bimU.AggregateFunctionsEnum.AVG;
```

### Viewer Class
This is the entry point to all bimU.io Viewer API functions that are listed in the [API Reference](/developer/api-reference). Dot key is the best exploration tool. Viewer configuration object must be passed into the Viewer's constructor. DOM element ID must be specified to contain the viewer component. The initialize method must be called before using other functions. The ```viewer``` variable used everywhere in our documentation literally refers to an instance of the ```Viewer``` class.

``` javascript
let viewerConfigs = {
    domElementId: "viewer",
    showFPS: false,
    showUI: true
};
let viewer = new bimU.Viewer(viewerConfigs);
viewer.initialize();			
```

### Load Model
The ```loadModel``` method loads full model geometry in the viewer container (i.e., a ```<div>``` element). Model ID must be specified in a model configuration object and can be found from the bimU.io Shared Link ```https://viewer.bimu.io/share/models/YOUR_MODEL_ID_IS_HERE```. Either access token or password must be specified depending on what authentication method used.

``` javascript
let modelConfigs = {
    modelId: "YOUR_MODEL_ID",
    accessToken: "ACCESS_TOKEN",
    password: "YOUR_MODEL_PASSWORD"
};
viewer.loadModel(modelConfigs, onPorgress, onLoaded, onError);			
```

### Release Resource
The dispose method can be called to free resources and reset configuration.

``` javascript
viewer.dispose();
```