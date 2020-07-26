# Initialisation
Dependencies

### bimU Namespace

``` javascript
// Initialise a class
let propertySelector = new bimU.PropertySelector("Text", "Mark");
// Enum
let func = bimU.AggregateFunctionsEnum.AVG;
```

### Viewer Class

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

``` javascript
let modelConfigs = {
    modelId: "",
    accessToken: "",
    password: "",
    baseUrl: "https://viewer.bimu.io/rest/api/v1"
};
viewer.loadModel(modelConfigs, onPorgress, onLoaded, onError);			
```

### Release Resource
Performs application-defined tasks associated with freeing, releasing, or resetting unmanaged resources.
``` javascript
viewer.dispose();
```