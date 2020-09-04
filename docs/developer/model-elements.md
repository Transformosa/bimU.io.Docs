# Model elements
This section summarises how to control the states of model elements in the viewer component, such as selection, visibility, appearance, etc. If you want to retrieve element data from bimU.io server, such as element properties, database query, etc., please refer to the next section [BIM Database](/developer/bim-database).

Every BIM authoring tool has its own mechanism to track and manage model element identifiers, such as element ID, unique ID, object ID, instance GUID, GUID, etc. To avoid confusion, bimU.io uses **element index** which is an integer value for sorting model elements internally. Every model element in bimU.io has a unique element index and therefore serves as an identifier for manipulating model elements.

### Selection
To know what model elements are currently selected by user, call the ```getElementIndicesBySelection``` function. You can use the ```anyElementSelected``` function to check if there's any selected model element beforehand. To clear current selection, call the ```unselectAllElements``` function.

### Visibility
The ```hideSelectedElements``` function and the ```isolateSelectedElements``` function are useful to control visibility of currently selected model elements. The former can make them invisible, while the latter can make them visible but hide all other model elements. If you need to hide or unhide specific model elements, call the ```setVisibility``` function. The ```invertOthers``` argument can set all other model elements to an opposite value. For example, to isolate element indices from 0 to 4:

``` javascript
// Make element indices 0 to 4 visible and hide all the rest
viewer.setVisibility([0, 1, 2, 3, 4], true, true);
```

There are two functions that can restore a model to its original state, i.e., all model elements are visible. The ```unhideAllElements``` function is self-explanatory. The ```resetVisibility``` function will not only unhide all elements but also clear current section box.

### Color Override
Occasionally you might need to change color for some model elements. For example, highlighting a clash, categorising by disciplines, etc. The ```setColor``` function allows to override original color of model elements. Below example highlights element indices from 0 to 4 in red. Calling the ```resetColor``` function will restore original colors.

``` javascript
// Element indices 0 to 4 will become red
viewer.setColor([0, 1, 2, 3, 4], new THREE.Color(0xff0000));
```

### Geometry
To duplicate geometry of a model element, the ```getGeometry``` function returns primitive geometry as a Three.js [BufferGeometry](https://threejs.org/docs/#api/en/core/BufferGeometry) object. Some relevant functions are also based on geometric conditions of model elements, such as ```getLocation```, ```getBoundingBox```, ```getBoundingBoxBySelection```, ```toggleWireframeMode```, etc.
