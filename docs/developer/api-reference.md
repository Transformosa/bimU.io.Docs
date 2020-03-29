## Classes

<dl>
<dt><a href="#Viewer">Viewer</a> ⇐ <code>THREE.EventDispatcher</code></dt>
<dd></dd>
</dl>

## Typedefs

<dl>
<dt><a href="#ViewerConfiguration">ViewerConfiguration</a> : <code>Object</code></dt>
<dd><p>Configuation object used to initialise bimU.io Viewer.</p>
</dd>
<dt><a href="#Viewpoint">Viewpoint</a> : <code>Object</code></dt>
<dd><p>BCF-compatible camera viewpoint.</p>
</dd>
<dt><a href="#onProgressCallback">onProgressCallback</a> : <code>function</code></dt>
<dd><p>This callback reports model loading progress.</p>
</dd>
</dl>

<a name="Viewer"></a>

## Viewer ⇐ <code>THREE.EventDispatcher</code>
**Kind**: global class  
**Extends**: <code>THREE.EventDispatcher</code>  

* [Viewer](#Viewer) ⇐ <code>THREE.EventDispatcher</code>
    * [new Viewer(configs)](#new_Viewer_new)
    * [.initialize()](#Viewer+initialize)
    * [.setViewpoint(viewpointObject)](#Viewer+setViewpoint)
    * [.getViewpoint()](#Viewer+getViewpoint) ⇒ [<code>Viewpoint</code>](#Viewpoint)
    * [.setProjectionMode(mode, value)](#Viewer+setProjectionMode)
    * [.isPerspectiveMode()](#Viewer+isPerspectiveMode) ⇒ <code>boolean</code>
    * [.switchSectionbox()](#Viewer+switchSectionbox)
    * [.sectionAroundSelection()](#Viewer+sectionAroundSelection)
    * [.anyElementSelected(showWarning)](#Viewer+anyElementSelected) ⇒ <code>boolean</code>
    * [.orientToView(viewe)](#Viewer+orientToView)
    * [.zoomToFit()](#Viewer+zoomToFit)
    * [.zoomToSelection()](#Viewer+zoomToSelection)
    * [.getBoundingBoxBySelectedElements()](#Viewer+getBoundingBoxBySelectedElements) ⇒ <code>THREE.Box3</code>
    * [.zoomToObject(object3D)](#Viewer+zoomToObject)
    * [.loadModel(modelConfigs, onProgress, onLoaded, onError)](#Viewer+loadModel)
    * [.unselectAllElements()](#Viewer+unselectAllElements)
    * [.unhideAllElements()](#Viewer+unhideAllElements)
    * [.resetVisibility()](#Viewer+resetVisibility)
    * [.setVisibility(elementIndices, isVisible)](#Viewer+setVisibility)
    * [.hideSelectedElements()](#Viewer+hideSelectedElements)
    * [.isPointInSectionBox(point)](#Viewer+isPointInSectionBox)
    * [.getFileProperties(onSuccess, onError)](#Viewer+getFileProperties) ⇒ <code>Object</code>
    * [.getModelMetadata(onSuccess, onError)](#Viewer+getModelMetadata) ⇒ <code>Object</code>
    * [.getElementDataByIndex(elementIndex, onSuccess, onError)](#Viewer+getElementDataByIndex) ⇒ <code>Object</code>
    * [.toggleFullscreen()](#Viewer+toggleFullscreen)
    * [.readCoordinates()](#Viewer+readCoordinates)
    * [.measureDistance()](#Viewer+measureDistance)
    * [.measureHeight()](#Viewer+measureHeight)
    * [.measureAngle()](#Viewer+measureAngle)
    * [.measureArea()](#Viewer+measureArea)
    * [.clearAllMeasurements()](#Viewer+clearAllMeasurements)
    * [.setColor(elementIndices, color, transparency)](#Viewer+setColor)
    * [.setTexture(elementIndices, texture)](#Viewer+setTexture)
    * [.addObject(object3D)](#Viewer+addObject) ⇒ <code>string</code>
    * [.removeObject(objectId)](#Viewer+removeObject)
    * [.addTag(type, text, location)](#Viewer+addTag) ⇒ <code>string</code>
    * [.removeTag(tagId)](#Viewer+removeTag)
    * [.getGeometry(elementIndex)](#Viewer+getGeometry) ⇒ <code>THREE.Geometry</code>
    * [.getLocation(elementIndex)](#Viewer+getLocation) ⇒ <code>THREE.Vector3</code>
    * [.getSelectedElementIndices()](#Viewer+getSelectedElementIndices) ⇒ <code>Array.&lt;number&gt;</code>
    * [.addCustomAction(name, tooltip, icon, callback)](#Viewer+addCustomAction)
    * [.removeCustomAction(name)](#Viewer+removeCustomAction)
    * [.setBackgroundColor(color)](#Viewer+setBackgroundColor)
    * [.toggleWireframeMode()](#Viewer+toggleWireframeMode)
    * [.getElementDataByFilter(filter, properties, isDistinct)](#Viewer+getElementDataByFilter) ⇒ <code>Object</code>
    * [.getElementDataByElementId(elementIdArray, properties)](#Viewer+getElementDataByElementId) ⇒ <code>Object</code>
    * [.getElementDataByUniqueId(uniqueIdArray, properties)](#Viewer+getElementDataByUniqueId) ⇒ <code>Object</code>
    * [.dispose()](#Viewer+dispose)

<a name="new_Viewer_new"></a>

### new Viewer(configs)
bimU.io Viewer main application. You should always create an instance of Viewer by passing the ViewerConfiguration object into the constructor.


| Param | Type | Description |
| --- | --- | --- |
| configs | [<code>ViewerConfiguration</code>](#ViewerConfiguration) | Viewer configuation object. See [ViewerConfiguration](#ViewerConfiguration). |

**Example**  
```js
let viewerConfigs = {
    domElementId: "viewer",
    accessToken: null,
    baseUrl: "https://viewer.bimu.io/rest/api/v1",
    THREE: null,
    showFPS: true,
    showUI: false
};
let viewer = new bimU.Viewer(viewerConfigs);
```
<a name="Viewer+initialize"></a>

### viewer.initialize()
You must call this method before using any other methods of Viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+setViewpoint"></a>

### viewer.setViewpoint(viewpointObject)
Set camera viewpoint and clipping planes.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**See**: [BCF Documentation](https://github.com/buildingSMART/BCF-XML/tree/release_2_1/Documentation#visualization-information-bcfv-file)  

| Param | Type | Description |
| --- | --- | --- |
| viewpointObject | [<code>Viewpoint</code>](#Viewpoint) | The BCF compatible viewpoint definition. See [Viewpoint](#Viewpoint). |

<a name="Viewer+getViewpoint"></a>

### viewer.getViewpoint() ⇒ [<code>Viewpoint</code>](#Viewpoint)
Get camera viewpoint and clipping planes.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: [<code>Viewpoint</code>](#Viewpoint) - The BCF compatible viewpoint definition. See [Viewpoint](#Viewpoint).  
**See**: [BCF Documentation](https://github.com/buildingSMART/BCF-XML/tree/release_2_1/Documentation#visualization-information-bcfv-file)  
<a name="Viewer+setProjectionMode"></a>

### viewer.setProjectionMode(mode, value)
This method changes camera parameters directly.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| mode | <code>CameraTypesEnum</code> | Perspective camera or orthographic camera. |
| value | <code>number</code> | Field of View or View to World Scale. |

<a name="Viewer+isPerspectiveMode"></a>

### viewer.isPerspectiveMode() ⇒ <code>boolean</code>
This is a helper method for checking camera type.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>boolean</code> - Whether current camera is a perspective one.  
<a name="Viewer+switchSectionbox"></a>

### viewer.switchSectionbox()
This method toggles section box visibility.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+sectionAroundSelection"></a>

### viewer.sectionAroundSelection()
This method creates a section box around current selection.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+anyElementSelected"></a>

### viewer.anyElementSelected(showWarning) ⇒ <code>boolean</code>
This is a helper method for checking if there's any element selected.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>boolean</code> - Whether at least one element selected.  

| Param | Type | Description |
| --- | --- | --- |
| showWarning | <code>boolean</code> | Whether an event should be dispathed if there's no element selected. |

<a name="Viewer+orientToView"></a>

### viewer.orientToView(viewe)
This method aligns current camera to an orthogonal view.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| viewe | <code>ViewOrientation</code> | Top, Bottom, Front, Back, Left, Right. |

<a name="Viewer+zoomToFit"></a>

### viewer.zoomToFit()
This method zooms model extent to fit current viewport.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+zoomToSelection"></a>

### viewer.zoomToSelection()
This method moves camera to focus on current selection.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+getBoundingBoxBySelectedElements"></a>

### viewer.getBoundingBoxBySelectedElements() ⇒ <code>THREE.Box3</code>
This method returns a bounding box of selected elements.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>THREE.Box3</code> - Represents an axis-aligned bounding box (AABB) in 3D space.  
<a name="Viewer+zoomToObject"></a>

### viewer.zoomToObject(object3D)
This method moves camera to focus on a particular 3D object.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| object3D | <code>THREE.Object3D</code> | The base class for most objects in Three.js. |

<a name="Viewer+loadModel"></a>

### viewer.loadModel(modelConfigs, onProgress, onLoaded, onError)
Load model from bimU.io

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| modelConfigs | <code>object</code> | Model configuration object. |
| onProgress | [<code>onProgressCallback</code>](#onProgressCallback) | Callback when model is being downloaded. |
| onLoaded | <code>onLoadedCallback</code> | Callback when model is fully loaded. |
| onError | <code>onErrorCallback</code> | Callback when an error occurs. |

<a name="Viewer+unselectAllElements"></a>

### viewer.unselectAllElements()
This method unselects all selected elements.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+unhideAllElements"></a>

### viewer.unhideAllElements()
This method make all hidden elements visible.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+resetVisibility"></a>

### viewer.resetVisibility()
This method unhide all elements and clear all section planes.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+setVisibility"></a>

### viewer.setVisibility(elementIndices, isVisible)
This method makes elements hidden or visible.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| elementIndices | <code>Array.&lt;number&gt;</code> | An array of element indices. |
| isVisible | <code>boolean</code> | True is visible. False is hidden. |

<a name="Viewer+hideSelectedElements"></a>

### viewer.hideSelectedElements()
This method make all selected elements invisible.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+isPointInSectionBox"></a>

### viewer.isPointInSectionBox(point)
This method checks whether a 3D point is within the current section box.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| point | <code>THREE.Vector3</code> | A 3D point. |

<a name="Viewer+getFileProperties"></a>

### viewer.getFileProperties(onSuccess, onError) ⇒ <code>Object</code>
This method retrieves file properties from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>Object</code> - File property object.  

| Param | Type | Description |
| --- | --- | --- |
| onSuccess | <code>onSuccessCallback</code> | Callback when data is received. |
| onError | <code>onErrorCallback</code> | Callback when an error occurs. |

<a name="Viewer+getModelMetadata"></a>

### viewer.getModelMetadata(onSuccess, onError) ⇒ <code>Object</code>
This method retrieves model metadata from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>Object</code> - Model metadata object.  

| Param | Type | Description |
| --- | --- | --- |
| onSuccess | <code>onSuccessCallback</code> | Callback when data is received. |
| onError | <code>onErrorCallback</code> | Callback when an error occurs. |

<a name="Viewer+getElementDataByIndex"></a>

### viewer.getElementDataByIndex(elementIndex, onSuccess, onError) ⇒ <code>Object</code>
This method retrieves model element data (Revit parameters, Navisworks properties, etc.) from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>Object</code> - Element data object.  

| Param | Type | Description |
| --- | --- | --- |
| elementIndex | <code>number</code> | Element index. |
| onSuccess | <code>onSuccessCallback</code> | Callback when data is received. |
| onError | <code>onErrorCallback</code> | Callback when an error occurs. |

<a name="Viewer+toggleFullscreen"></a>

### viewer.toggleFullscreen()
This method enables or exits full screen mode.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+readCoordinates"></a>

### viewer.readCoordinates()
This method starts user interaction to read XYZ coordinates.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+measureDistance"></a>

### viewer.measureDistance()
This method starts user interaction to measure distance point by point.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+measureHeight"></a>

### viewer.measureHeight()
This method starts user interaction to measure height by three points.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+measureAngle"></a>

### viewer.measureAngle()
This method starts user interaction to measure angles by a triangle formed by three points.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+measureArea"></a>

### viewer.measureArea()
This method starts user interaction to measure area by a polygon.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+clearAllMeasurements"></a>

### viewer.clearAllMeasurements()
This method removes all current measurements shown in the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+setColor"></a>

### viewer.setColor(elementIndices, color, transparency)
This method sets element color.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| elementIndices | <code>Array.&lt;number&gt;</code> | An array of element indices. |
| color | <code>THREE.Color</code> | Color object in RGB. |
| transparency | <code>number</code> | 0 is Opaque. 1 is invisible. |

<a name="Viewer+setTexture"></a>

### viewer.setTexture(elementIndices, texture)
This method adds texture to elements.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| elementIndices | <code>Array.&lt;number&gt;</code> | An array of element indices. |
| texture | <code>THREE.Texture</code> | Texture object. |

<a name="Viewer+addObject"></a>

### viewer.addObject(object3D) ⇒ <code>string</code>
This method adds an arbitrary 3D object to the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>string</code> - UUID of created Object3D.  

| Param | Type | Description |
| --- | --- | --- |
| object3D | <code>THREE.Object3D</code> | Three.js Object3D object. |

<a name="Viewer+removeObject"></a>

### viewer.removeObject(objectId)
This method removes an existing 3D object from the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| objectId | <code>string</code> | Three.js Object3D UUID. |

<a name="Viewer+addTag"></a>

### viewer.addTag(type, text, location) ⇒ <code>string</code>
This method adds a 3D sprite to a particular location.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>string</code> - UUID of created Object3D.  

| Param | Type | Description |
| --- | --- | --- |
| type | <code>string</code> | Tag type. |
| text | <code>string</code> | Text to display in tag. |
| location | <code>THREE.Vector3</code> | A 3D point where this tag should be placed. |

<a name="Viewer+removeTag"></a>

### viewer.removeTag(tagId)
This method removes an existing tag from the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| tagId | <code>string</code> | Three.js Object3D UUID. |

<a name="Viewer+getGeometry"></a>

### viewer.getGeometry(elementIndex) ⇒ <code>THREE.Geometry</code>
This method returns primitive geometry of a particular element.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>THREE.Geometry</code> - Three.js Geometry object.  

| Param | Type | Description |
| --- | --- | --- |
| elementIndex | <code>number</code> | Element index. |

<a name="Viewer+getLocation"></a>

### viewer.getLocation(elementIndex) ⇒ <code>THREE.Vector3</code>
This method returns the center point of a particular element.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>THREE.Vector3</code> - Three.js Vector3 object.  

| Param | Type | Description |
| --- | --- | --- |
| elementIndex | <code>number</code> | Element index. |

<a name="Viewer+getSelectedElementIndices"></a>

### viewer.getSelectedElementIndices() ⇒ <code>Array.&lt;number&gt;</code>
This method returns the center point of a particular element.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>Array.&lt;number&gt;</code> - An array of element indices.  
<a name="Viewer+addCustomAction"></a>

### viewer.addCustomAction(name, tooltip, icon, callback)
This method creates a menu item on the user interface of the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | Name of custom action. |
| tooltip | <code>string</code> | Short description. |
| icon | <code>string</code> | Icon string. |
| callback | <code>function</code> | A callback function when the menu item is clicked. |

<a name="Viewer+removeCustomAction"></a>

### viewer.removeCustomAction(name)
This method removes an existing menu item.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | Name of custom action. |

<a name="Viewer+setBackgroundColor"></a>

### viewer.setBackgroundColor(color)
This method sets background color of the viewer canvas.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| color | <code>THREE.Color</code> | Color object in RGB. |

<a name="Viewer+toggleWireframeMode"></a>

### viewer.toggleWireframeMode()
This method turns on or off wireframe mode.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+getElementDataByFilter"></a>

### viewer.getElementDataByFilter(filter, properties, isDistinct) ⇒ <code>Object</code>
This method retrieves element data based on a custom element filter from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>Object</code> - Element data object.  

| Param | Type | Description |
| --- | --- | --- |
| filter | <code>string</code> | A query string of filter. |
| properties | <code>Array.&lt;string&gt;</code> | An array of element properties to return. |
| isDistinct | <code>boolean</code> | Whether return only unique values. |

<a name="Viewer+getElementDataByElementId"></a>

### viewer.getElementDataByElementId(elementIdArray, properties) ⇒ <code>Object</code>
This method retrieves element data by an array of element IDs from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>Object</code> - Element data object.  

| Param | Type | Description |
| --- | --- | --- |
| elementIdArray | <code>Array.&lt;string&gt;</code> | An array of element IDs. |
| properties | <code>Array.&lt;string&gt;</code> | An array of element properties to return. |

<a name="Viewer+getElementDataByUniqueId"></a>

### viewer.getElementDataByUniqueId(uniqueIdArray, properties) ⇒ <code>Object</code>
This method retrieves element data by an array of unique IDs from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>Object</code> - Element data object.  

| Param | Type | Description |
| --- | --- | --- |
| uniqueIdArray | <code>Array.&lt;string&gt;</code> | An array of unique IDs. |
| properties | <code>Array.&lt;string&gt;</code> | An array of element properties to return. |

<a name="Viewer+dispose"></a>

### viewer.dispose()
This method destroy this Viewer instance and release all resources.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="ViewerConfiguration"></a>

## ViewerConfiguration : <code>Object</code>
Configuation object used to initialise bimU.io Viewer.

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| domElementId | <code>string</code> | DIV element ID |
| accessToken | <code>string</code> | Access token |
| baseUrl | <code>string</code> | Override base URL of bimU.io server. |
| showFPS | <code>boolean</code> | Whether show FPS meter. |
| showUI | <code>boolean</code> | Whether show UI. |

<a name="Viewpoint"></a>

## Viewpoint : <code>Object</code>
BCF-compatible camera viewpoint.

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| camera | <code>string</code> | Perspective camera or orthographic camera. |
| clippingPlanes | <code>string</code> | Clipping plane definition. |
| originatingSystem | <code>string</code> | Where this viewpoint was created from. |

<a name="onProgressCallback"></a>

## onProgressCallback : <code>function</code>
This callback reports model loading progress.

**Kind**: global typedef  

| Param | Type | Description |
| --- | --- | --- |
| type | <code>string</code> | Event type. |
| progress | <code>number</code> | Model loading progress in percentage. |

