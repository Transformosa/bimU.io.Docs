## Classes

<dl>
<dt><a href="#Viewer">Viewer</a> ⇐ <code>THREE.EventDispatcher</code></dt>
<dd></dd>
<dt><a href="#PropertyFilter">PropertyFilter</a></dt>
<dd></dd>
<dt><a href="#PropertySelector">PropertySelector</a></dt>
<dd></dd>
<dt><a href="#AggregateFunctionsEnum">AggregateFunctionsEnum</a></dt>
<dd></dd>
<dt><a href="#CameraTypesEnum">CameraTypesEnum</a></dt>
<dd></dd>
<dt><a href="#DataTypesEnum">DataTypesEnum</a></dt>
<dd></dd>
<dt><a href="#EventsEnum">EventsEnum</a></dt>
<dd></dd>
<dt><a href="#OperatorsEnum">OperatorsEnum</a></dt>
<dd></dd>
</dl>

## Typedefs

<dl>
<dt><a href="#ViewerConfiguration">ViewerConfiguration</a> : <code>Object</code></dt>
<dd><p>Configuation object used to initialise bimU.io Viewer.</p>
</dd>
<dt><a href="#Viewpoint">Viewpoint</a> : <code>Object</code></dt>
<dd><p>BCF-compatible viewpoint object.</p>
</dd>
<dt><a href="#Camera">Camera</a> : <code>Object</code></dt>
<dd><p>BCF-compatible camera object.</p>
</dd>
<dt><a href="#ClippingPlane">ClippingPlane</a> : <code>Object</code></dt>
<dd><p>BCF-compatible clipping plane object.</p>
</dd>
<dt><a href="#XYZ">XYZ</a> : <code>Object</code></dt>
<dd><p>BCF-compatible XYZ object.</p>
</dd>
<dt><a href="#TagOptions">TagOptions</a> : <code>Object</code></dt>
<dd><p>Display options for Tag.</p>
</dd>
</dl>

<a name="Viewer"></a>

## Viewer ⇐ <code>THREE.EventDispatcher</code>
**Kind**: global class  
**Extends**: <code>THREE.EventDispatcher</code>  

* [Viewer](#Viewer) ⇐ <code>THREE.EventDispatcher</code>
    * [new Viewer(configs)](#new_Viewer_new)
    * [.showDialog(title, body, closeButtonText, okButtonText, [okButtonCallback], [dismissible])](#Viewer+showDialog)
    * [.closeDialog()](#Viewer+closeDialog)
    * [.showHelp()](#Viewer+showHelp)
    * [.showElementInformation()](#Viewer+showElementInformation)
    * [.initialize()](#Viewer+initialize)
    * [.setViewpoint(viewpointObject)](#Viewer+setViewpoint)
    * [.getViewpoint()](#Viewer+getViewpoint) ⇒ [<code>Viewpoint</code>](#Viewpoint)
    * [.setSectionBox(min, max)](#Viewer+setSectionBox)
    * [.setSectionBoxMode(mode)](#Viewer+setSectionBoxMode)
    * [.setProjectionMode(mode, value)](#Viewer+setProjectionMode)
    * [.isPerspectiveMode()](#Viewer+isPerspectiveMode) ⇒ <code>boolean</code>
    * [.toggleSectionbox([isVisible])](#Viewer+toggleSectionbox)
    * [.sectionAroundSelection()](#Viewer+sectionAroundSelection)
    * [.anyElementSelected(showWarning)](#Viewer+anyElementSelected) ⇒ <code>boolean</code>
    * [.alignToView(viewOrientation)](#Viewer+alignToView)
    * [.zoomToFit()](#Viewer+zoomToFit)
    * [.zoomToSelection()](#Viewer+zoomToSelection)
    * [.getBoundingBoxBySelection()](#Viewer+getBoundingBoxBySelection) ⇒ <code>THREE.Box3</code>
    * [.zoomToObject(object3D)](#Viewer+zoomToObject)
    * [.loadModel(modelConfigs, onProgress, onLoaded, onError)](#Viewer+loadModel)
    * [.unselectAllElements()](#Viewer+unselectAllElements)
    * [.unhideAllElements()](#Viewer+unhideAllElements)
    * [.resetVisibility()](#Viewer+resetVisibility)
    * [.setVisibility(elementIndices, isVisible, [invertOthers])](#Viewer+setVisibility)
    * [.hideSelectedElements()](#Viewer+hideSelectedElements)
    * [.isolateSelectedElements()](#Viewer+isolateSelectedElements)
    * [.isPointInSectionBox(point)](#Viewer+isPointInSectionBox)
    * [.clearAllColorOverrides()](#Viewer+clearAllColorOverrides)
    * [.getFileProperties(onSuccess, onError)](#Viewer+getFileProperties)
    * [.getModelMetadata(onSuccess, onError)](#Viewer+getModelMetadata)
    * [.getElementDataByIndex(elementIndex, onSuccess, onError)](#Viewer+getElementDataByIndex)
    * [.toggleFullscreen([isFullScreen])](#Viewer+toggleFullscreen)
    * [.readCoordinates()](#Viewer+readCoordinates)
    * [.measureDistance()](#Viewer+measureDistance)
    * [.measureHeight()](#Viewer+measureHeight)
    * [.measureAngle()](#Viewer+measureAngle)
    * [.measureArea()](#Viewer+measureArea)
    * [.clearAllMeasurements()](#Viewer+clearAllMeasurements)
    * [.setColor(elementIndices, color)](#Viewer+setColor)
    * [.setTexture(elementIndices, texture)](#Viewer+setTexture)
    * [.addObject(object3D)](#Viewer+addObject) ⇒ <code>string</code>
    * [.removeObject(objectId)](#Viewer+removeObject)
    * [.addTag(text, location, [options], [onClick])](#Viewer+addTag) ⇒ <code>string</code>
    * [.removeTag(tagId)](#Viewer+removeTag)
    * [.getGeometry(elementIndex)](#Viewer+getGeometry) ⇒ <code>THREE.BufferGeometry</code>
    * [.getBoundingBox(elementIndices)](#Viewer+getBoundingBox) ⇒ <code>THREE.Box3</code>
    * [.getLocation(elementIndex)](#Viewer+getLocation) ⇒ <code>THREE.Vector3</code>
    * [.getElementIndicesBySelection()](#Viewer+getElementIndicesBySelection) ⇒ <code>Array.&lt;number&gt;</code>
    * [.addCustomButton(domElementId, icon, color, tooltip, callback)](#Viewer+addCustomButton)
    * [.removeDomElement(domElementId)](#Viewer+removeDomElement)
    * [.setBackgroundColor(color)](#Viewer+setBackgroundColor)
    * [.toggleWireframeMode([isWireframe])](#Viewer+toggleWireframeMode)
    * [.getScreenshot(openInNewWindow)](#Viewer+getScreenshot) ⇒ <code>string</code>
    * [.getElementDataByQuery(filterExpression, selectExpression, limit, onSuccess, onError)](#Viewer+getElementDataByQuery)
    * [.getElementDataByProperty(propertyFilters, propertySelectors, limit, onSuccess, onError)](#Viewer+getElementDataByProperty)
    * [.aggregateElementProperty(propertyFilters, propertyToAggregate, aggregateFunction, onSuccess, onError)](#Viewer+aggregateElementProperty)
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
    THREE: null,
    showFPS: true,
    showUI: false
};
let viewer = new bimU.Viewer(viewerConfigs);
```
<a name="Viewer+showDialog"></a>

### viewer.showDialog(title, body, closeButtonText, okButtonText, [okButtonCallback], [dismissible])
Displays a modal dialog with custom UI.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| title | <code>string</code> |  | Modal dialog title in plain text or HTML. |
| body | <code>string</code> |  | Modal dialog body in plain text or HTML. |
| closeButtonText | <code>string</code> |  | Display text of the Close button. Passing a null value will hide the button. |
| okButtonText | <code>string</code> |  | Display text of the OK button. Passing a null value will hide the button. |
| [okButtonCallback] | <code>function</code> |  | Callback function when the OK button is clicked. |
| [dismissible] | <code>boolean</code> | <code>true</code> | Allow modal to be dismissed by keyboard or overlay click. |

<a name="Viewer+closeDialog"></a>

### viewer.closeDialog()
Closes custom modal dialog.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+showHelp"></a>

### viewer.showHelp()
Displays user instructions in a modal dialog.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+showElementInformation"></a>

### viewer.showElementInformation()
Displays selected element properties in a modal dialog.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+initialize"></a>

### viewer.initialize()
Initializes bimU.io Viewer. This function must be called before using any other functions.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+setViewpoint"></a>

### viewer.setViewpoint(viewpointObject)
Sets camera viewpoint and clipping planes.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**See**: [BCF Documentation](https://github.com/buildingSMART/BCF-XML/tree/release_2_1/Documentation#visualization-information-bcfv-file)  

| Param | Type | Description |
| --- | --- | --- |
| viewpointObject | [<code>Viewpoint</code>](#Viewpoint) | The BCF compatible viewpoint definition. See [Viewpoint](#Viewpoint). |

<a name="Viewer+getViewpoint"></a>

### viewer.getViewpoint() ⇒ [<code>Viewpoint</code>](#Viewpoint)
Gets camera viewpoint and clipping planes.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: [<code>Viewpoint</code>](#Viewpoint) - The BCF compatible viewpoint definition. See [Viewpoint](#Viewpoint).  
**See**: [BCF Documentation](https://github.com/buildingSMART/BCF-XML/tree/release_2_1/Documentation#visualization-information-bcfv-file)  
<a name="Viewer+setSectionBox"></a>

### viewer.setSectionBox(min, max)
Sets the section box orthogonally.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| min | <code>THREE.Vector3</code> | Minimum coordinates (lower-left-rear corner of the box). |
| max | <code>THREE.Vector3</code> | Maximum coordinates (upper-right-front corner of the box). |

<a name="Viewer+setSectionBoxMode"></a>

### viewer.setSectionBoxMode(mode)
Sets the transformation mode of the section box.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| mode | <code>string</code> | The current transformation mode. Possible values are "custom", "translate", "rotate", and "scale". Default is "custom". |

<a name="Viewer+setProjectionMode"></a>

### viewer.setProjectionMode(mode, value)
Changes camera parameters directly.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| mode | [<code>CameraTypesEnum</code>](#CameraTypesEnum) | Perspective camera or orthographic camera. |
| value | <code>number</code> | Field of View or View to World Scale. |

<a name="Viewer+isPerspectiveMode"></a>

### viewer.isPerspectiveMode() ⇒ <code>boolean</code>
Checks camera type.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>boolean</code> - Whether current camera is a perspective one.  
<a name="Viewer+toggleSectionbox"></a>

### viewer.toggleSectionbox([isVisible])
Toggles section box visibility.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| [isVisible] | <code>boolean</code> | Use true to show the section box or false to hide it. It toggles the visibility if the parameter is not set. |

<a name="Viewer+sectionAroundSelection"></a>

### viewer.sectionAroundSelection()
Creates a section box around current selection.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+anyElementSelected"></a>

### viewer.anyElementSelected(showWarning) ⇒ <code>boolean</code>
Checks if there's any element selected.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>boolean</code> - Whether at least one element selected.  

| Param | Type | Description |
| --- | --- | --- |
| showWarning | <code>boolean</code> | Whether an event should be dispathed if there's no element selected. |

<a name="Viewer+alignToView"></a>

### viewer.alignToView(viewOrientation)
Aligns current camera to an orthogonal view.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| viewOrientation | <code>string</code> | Valid values: 'top', 'bottom', 'front', 'back', 'left', 'right'. |

<a name="Viewer+zoomToFit"></a>

### viewer.zoomToFit()
Zooms model extent to fit current viewport.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+zoomToSelection"></a>

### viewer.zoomToSelection()
Moves camera to focus on current selection.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+getBoundingBoxBySelection"></a>

### viewer.getBoundingBoxBySelection() ⇒ <code>THREE.Box3</code>
Returns a bounding box of selected elements.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>THREE.Box3</code> - Represents an axis-aligned bounding box (AABB) in 3D space.  
<a name="Viewer+zoomToObject"></a>

### viewer.zoomToObject(object3D)
Moves camera to focus on a particular 3D object.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| object3D | <code>THREE.Object3D</code> | The base class for most objects in Three.js. |

<a name="Viewer+loadModel"></a>

### viewer.loadModel(modelConfigs, onProgress, onLoaded, onError)
Loads model from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| modelConfigs | <code>object</code> | Model configuration object. |
| onProgress | <code>function</code> | Callback when model is being downloaded. |
| onLoaded | <code>function</code> | Callback when model is fully loaded. |
| onError | <code>function</code> | Callback when an error occurs. |

<a name="Viewer+unselectAllElements"></a>

### viewer.unselectAllElements()
Unselects all selected elements.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+unhideAllElements"></a>

### viewer.unhideAllElements()
Makes all hidden elements visible.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+resetVisibility"></a>

### viewer.resetVisibility()
Unhides all elements and clears all section planes.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+setVisibility"></a>

### viewer.setVisibility(elementIndices, isVisible, [invertOthers])
Makes elements hidden or visible.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| elementIndices | <code>Array.&lt;number&gt;</code> | An array of element indices. |
| isVisible | <code>boolean</code> | True is visible. False is hidden. |
| [invertOthers] | <code>boolean</code> | True to set all other elements inversely. Default is false. |

<a name="Viewer+hideSelectedElements"></a>

### viewer.hideSelectedElements()
Makes all selected elements invisible.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+isolateSelectedElements"></a>

### viewer.isolateSelectedElements()
Hides all unselected elements.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+isPointInSectionBox"></a>

### viewer.isPointInSectionBox(point)
Checks whether a 3D point is within the current section box.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| point | <code>THREE.Vector3</code> | A 3D point. |

<a name="Viewer+clearAllColorOverrides"></a>

### viewer.clearAllColorOverrides()
Removes color overrides from all elements.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+getFileProperties"></a>

### viewer.getFileProperties(onSuccess, onError)
Retrieves file properties from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| onSuccess | <code>function</code> | Callback when data is received. |
| onError | <code>function</code> | Callback when an error occurs. |

<a name="Viewer+getModelMetadata"></a>

### viewer.getModelMetadata(onSuccess, onError)
Retrieves model metadata from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| onSuccess | <code>function</code> | Callback when data is received. |
| onError | <code>function</code> | Callback when an error occurs. |

<a name="Viewer+getElementDataByIndex"></a>

### viewer.getElementDataByIndex(elementIndex, onSuccess, onError)
Retrieves model element data (Revit parameters, Navisworks properties, etc.) from bimU.io server.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| elementIndex | <code>number</code> | Element index. |
| onSuccess | <code>function</code> | Callback when data is received. |
| onError | <code>function</code> | Callback when an error occurs. |

<a name="Viewer+toggleFullscreen"></a>

### viewer.toggleFullscreen([isFullScreen])
Activates or exits full screen mode.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| [isFullScreen] | <code>boolean</code> | Use true to activate full screen or false to exit. It toggles the full screen mode if the parameter is not set. |

<a name="Viewer+readCoordinates"></a>

### viewer.readCoordinates()
Starts user interaction to read XYZ coordinates.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+measureDistance"></a>

### viewer.measureDistance()
Starts user interaction to measure distance point by point.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+measureHeight"></a>

### viewer.measureHeight()
Starts user interaction to measure height by three points.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+measureAngle"></a>

### viewer.measureAngle()
Starts user interaction to measure angles by a triangle formed by three points.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+measureArea"></a>

### viewer.measureArea()
Starts user interaction to measure area by a polygon.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+clearAllMeasurements"></a>

### viewer.clearAllMeasurements()
Removes all current measurements shown in the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="Viewer+setColor"></a>

### viewer.setColor(elementIndices, color)
Overrides element color.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| elementIndices | <code>Array.&lt;number&gt;</code> | An array of element indices. |
| color | <code>THREE.Color</code> | Three.js color object. |

<a name="Viewer+setTexture"></a>

### viewer.setTexture(elementIndices, texture)
WORK IN PROGRESS. Adds texture to elements.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| elementIndices | <code>Array.&lt;number&gt;</code> | An array of element indices. |
| texture | <code>THREE.Texture</code> | Texture object. |

<a name="Viewer+addObject"></a>

### viewer.addObject(object3D) ⇒ <code>string</code>
Adds an arbitrary 3D object to the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>string</code> - UUID of created Object3D.  

| Param | Type | Description |
| --- | --- | --- |
| object3D | <code>THREE.Object3D</code> | Three.js Object3D object. |

<a name="Viewer+removeObject"></a>

### viewer.removeObject(objectId)
Removes an existing 3D object from the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| objectId | <code>string</code> | Three.js Object3D UUID. |

<a name="Viewer+addTag"></a>

### viewer.addTag(text, location, [options], [onClick]) ⇒ <code>string</code>
This method adds a 3D sprite to a particular location.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>string</code> - UUID of created Object3D.  

| Param | Type | Description |
| --- | --- | --- |
| text | <code>string</code> | Text to display in tag. |
| location | <code>THREE.Vector3</code> | 3D point where tag is placed. |
| [options] | [<code>TagOptions</code>](#TagOptions) | Tag display options. |
| [onClick] | <code>function</code> | Callback function when tag is clicked. |

<a name="Viewer+removeTag"></a>

### viewer.removeTag(tagId)
Removes an existing tag from the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| tagId | <code>string</code> | Three.js Object3D UUID. |

<a name="Viewer+getGeometry"></a>

### viewer.getGeometry(elementIndex) ⇒ <code>THREE.BufferGeometry</code>
Returns primitive geometry of a particular model element.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>THREE.BufferGeometry</code> - Three.js BufferGeometry object.  

| Param | Type | Description |
| --- | --- | --- |
| elementIndex | <code>number</code> | Element index. |

<a name="Viewer+getBoundingBox"></a>

### viewer.getBoundingBox(elementIndices) ⇒ <code>THREE.Box3</code>
Returns the bounding box of particular model elements or the entire model if the parameter is not set.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>THREE.Box3</code> - Represents an axis-aligned bounding box (AABB) in 3D space.  

| Param | Type | Description |
| --- | --- | --- |
| elementIndices | <code>number</code> | Element index. |

<a name="Viewer+getLocation"></a>

### viewer.getLocation(elementIndex) ⇒ <code>THREE.Vector3</code>
Returns the center point of a particular model element.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>THREE.Vector3</code> - Three.js Vector3 object.  

| Param | Type | Description |
| --- | --- | --- |
| elementIndex | <code>number</code> | Element index. |

<a name="Viewer+getElementIndicesBySelection"></a>

### viewer.getElementIndicesBySelection() ⇒ <code>Array.&lt;number&gt;</code>
Returns indices of selected elements.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>Array.&lt;number&gt;</code> - An array of element indices.  
<a name="Viewer+addCustomButton"></a>

### viewer.addCustomButton(domElementId, icon, color, tooltip, callback)
Creates a custom button on the user interface of the viewer.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| domElementId | <code>string</code> | DOM element id to use for this button. |
| icon | <code>string</code> | Icon string. |
| color | <code>string</code> | CSS color keyword, RGBA, or Hex code. |
| tooltip | <code>string</code> | Short description. |
| callback | <code>function</code> | A callback function when this button is clicked. |

<a name="Viewer+removeDomElement"></a>

### viewer.removeDomElement(domElementId)
Removes an existing DOM element by its ID.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| domElementId | <code>string</code> | DOM element id to remove. |

<a name="Viewer+setBackgroundColor"></a>

### viewer.setBackgroundColor(color)
Sets background color of the viewer canvas.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| color | <code>number</code> | Hexadecimal color. E.g., 0xff0000. |

<a name="Viewer+toggleWireframeMode"></a>

### viewer.toggleWireframeMode([isWireframe])
Turns on or off wireframe mode.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| [isWireframe] | <code>boolean</code> | Use true to show wireframe or false to hide it. It toggles the wireframe mode if the parameter is not set. |

<a name="Viewer+getScreenshot"></a>

### viewer.getScreenshot(openInNewWindow) ⇒ <code>string</code>
Returns screenshot of the viewer canvas.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
**Returns**: <code>string</code> - A DOMString containing a data URI containing a representation of the screenshot.  

| Param | Type | Description |
| --- | --- | --- |
| openInNewWindow | <code>boolean</code> | Whether opens screenshot in a new window/tab. |

<a name="Viewer+getElementDataByQuery"></a>

### viewer.getElementDataByQuery(filterExpression, selectExpression, limit, onSuccess, onError)
Retrieves element data from bimU.io server based on a custom query expression.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| filterExpression | <code>string</code> | Filter expression string. |
| selectExpression | <code>string</code> | Select expression string. |
| limit | <code>number</code> | Limit on the number of elements returned. |
| onSuccess | <code>function</code> | Callback when data is received. |
| onError | <code>function</code> | Callback when an error occurs. |

<a name="Viewer+getElementDataByProperty"></a>

### viewer.getElementDataByProperty(propertyFilters, propertySelectors, limit, onSuccess, onError)
Retrieves element data by predefined property filters and selectors.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| propertyFilters | [<code>Array.&lt;PropertyFilter&gt;</code>](#PropertyFilter) | Array of property filters that look for elements satisfying specified conditions. |
| propertySelectors | [<code>Array.&lt;PropertySelector&gt;</code>](#PropertySelector) | Array of property selectors. Maximum of 5 properties to return. |
| limit | <code>number</code> | Limit on the number of elements returned. |
| onSuccess | <code>function</code> | Callback when data is received. |
| onError | <code>function</code> | Callback when an error occurs. |

<a name="Viewer+aggregateElementProperty"></a>

### viewer.aggregateElementProperty(propertyFilters, propertyToAggregate, aggregateFunction, onSuccess, onError)
Retrieves element data by predefined property filters and selectors.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  

| Param | Type | Description |
| --- | --- | --- |
| propertyFilters | [<code>Array.&lt;PropertyFilter&gt;</code>](#PropertyFilter) | Array of property filters. |
| propertyToAggregate | [<code>PropertySelector</code>](#PropertySelector) | Single property selector that will be aggregated. |
| aggregateFunction | [<code>AggregateFunctionsEnum</code>](#AggregateFunctionsEnum) | Limit on the number of elements returned. Default is COUNT. |
| onSuccess | <code>function</code> | Callback when data is received. |
| onError | <code>function</code> | Callback when an error occurs. |

<a name="Viewer+dispose"></a>

### viewer.dispose()
Destroys this Viewer instance and releases all resources.

**Kind**: instance method of [<code>Viewer</code>](#Viewer)  
<a name="PropertyFilter"></a>

## PropertyFilter
**Kind**: global class  

* [PropertyFilter](#PropertyFilter)
    * [new PropertyFilter(groupName, propertyName, propertyValue)](#new_PropertyFilter_new)
    * [.operator](#PropertyFilter+operator) : [<code>OperatorsEnum</code>](#OperatorsEnum)
    * [.groupName](#PropertyFilter+groupName) : <code>string</code>
    * [.propertyName](#PropertyFilter+propertyName) : <code>string</code>
    * [.propertyValue](#PropertyFilter+propertyValue) : <code>string</code> \| <code>Array.&lt;string&gt;</code> \| <code>number</code> \| <code>Array.&lt;number&gt;</code>
    * [.getExpressionString()](#PropertyFilter+getExpressionString) ⇒ <code>string</code>

<a name="new_PropertyFilter_new"></a>

### new PropertyFilter(groupName, propertyName, propertyValue)
This class is used to find elements by a property that satisfies the specified condition. It is similar to the SQL WHERE clause.


| Param | Type | Description |
| --- | --- | --- |
| groupName | <code>string</code> | Property group name. |
| propertyName | <code>string</code> | Property name. |
| propertyValue | <code>string</code> | Property value. |

**Example**  
```js
// Filter out elements that have a property called "Top Constrant" in a "Constraints" group and its value is equal to "Level 1".
let propertyFilter1 = new bimU.PropertyFilter("Constraints", "Top Constrant", "Level 1");
// Filter out elements that have a property called "Height" in a "Dimension" group and its value is greater than 12.34.
let propertyFilter2 = new bimU.PropertyFilter("Dimension", "Height", 12.34);
// Default operator is EQUAL_TO.
propertyFilter2.operator = bimU.OperatorsEnum.GREATER_THAN;
```
<a name="PropertyFilter+operator"></a>

### propertyFilter.operator : [<code>OperatorsEnum</code>](#OperatorsEnum)
An operator that determines how the property value is compared. Default is bimU.OperatorsEnum.EQUAL_TO.

**Kind**: instance property of [<code>PropertyFilter</code>](#PropertyFilter)  
<a name="PropertyFilter+groupName"></a>

### propertyFilter.groupName : <code>string</code>
Property group name

**Kind**: instance property of [<code>PropertyFilter</code>](#PropertyFilter)  
<a name="PropertyFilter+propertyName"></a>

### propertyFilter.propertyName : <code>string</code>
Property name.

**Kind**: instance property of [<code>PropertyFilter</code>](#PropertyFilter)  
<a name="PropertyFilter+propertyValue"></a>

### propertyFilter.propertyValue : <code>string</code> \| <code>Array.&lt;string&gt;</code> \| <code>number</code> \| <code>Array.&lt;number&gt;</code>
Property value. Use Array along with IN, NOT_IN, or BETWEEN operators.

**Kind**: instance property of [<code>PropertyFilter</code>](#PropertyFilter)  
<a name="PropertyFilter+getExpressionString"></a>

### propertyFilter.getExpressionString() ⇒ <code>string</code>
This method returns a SQL equivalent expression for the underlying filter.

**Kind**: instance method of [<code>PropertyFilter</code>](#PropertyFilter)  
**Returns**: <code>string</code> - SQL filter expression.  
<a name="PropertySelector"></a>

## PropertySelector
**Kind**: global class  

* [PropertySelector](#PropertySelector)
    * [new PropertySelector(groupName, propertyName)](#new_PropertySelector_new)
    * [.dataType](#PropertySelector+dataType) : [<code>DataTypesEnum</code>](#DataTypesEnum)
    * [.groupName](#PropertySelector+groupName) : <code>string</code>
    * [.propertyName](#PropertySelector+propertyName) : <code>string</code>
    * [.alias](#PropertySelector+alias) : <code>string</code>
    * [.getExpressionString()](#PropertySelector+getExpressionString) ⇒ <code>string</code>

<a name="new_PropertySelector_new"></a>

### new PropertySelector(groupName, propertyName)
This class is used to specify or restrict properties to return. It is similar to the SQL SELECT clause.


| Param | Type | Description |
| --- | --- | --- |
| groupName | <code>string</code> | Property group name. |
| propertyName | <code>string</code> | Property name. |

**Example**  
```js
// Return a property called "Top Offset" in a "Constraints" group.
let propertySelector1 = new bimU.PropertySelector("Constraints", "Top Offset");
// Default data type is STRING.
propertySelector1.type = bimU.DataTypesEnum.FLOAT;
// Return a property called "Mark" in a "Text" group.
let propertySelector2 = new bimU.PropertySelector("Text", "Mark");
// Rename the property name to "Wall Mark" when data is returned.
propertySelector2.alias = "Wall Mark";
```
<a name="PropertySelector+dataType"></a>

### propertySelector.dataType : [<code>DataTypesEnum</code>](#DataTypesEnum)
Data type casting/conversion. Default is bimU.DataTypesEnum.STRING.

**Kind**: instance property of [<code>PropertySelector</code>](#PropertySelector)  
<a name="PropertySelector+groupName"></a>

### propertySelector.groupName : <code>string</code>
Property group name

**Kind**: instance property of [<code>PropertySelector</code>](#PropertySelector)  
<a name="PropertySelector+propertyName"></a>

### propertySelector.propertyName : <code>string</code>
Property name.

**Kind**: instance property of [<code>PropertySelector</code>](#PropertySelector)  
<a name="PropertySelector+alias"></a>

### propertySelector.alias : <code>string</code>
Alias for renaming the property name. It is similar to the SQL AS command. Default is the same as the property name.

**Kind**: instance property of [<code>PropertySelector</code>](#PropertySelector)  
<a name="PropertySelector+getExpressionString"></a>

### propertySelector.getExpressionString() ⇒ <code>string</code>
This method returns a SQL equivalent expression for the underlying selector.

**Kind**: instance method of [<code>PropertySelector</code>](#PropertySelector)  
**Returns**: <code>string</code> - SQL select expression.  
<a name="AggregateFunctionsEnum"></a>

## AggregateFunctionsEnum
**Kind**: global class  
**Read only**: true  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| AVG | <code>string</code> | Calculate the average value of a numeric property. |
| COUNT | <code>string</code> | Get the number of matching elements. |
| MAX | <code>string</code> | Get the largest value of a numeric property. |
| MIN | <code>string</code> | Get the smallest value of a numeric property. |
| SUM | <code>string</code> | Calculate the total sum of a numeric property. |

<a name="new_AggregateFunctionsEnum_new"></a>

### new AggregateFunctionsEnum()
Enum for aggregate functions that perform a calculation on property values and return a single value.

<a name="CameraTypesEnum"></a>

## CameraTypesEnum
**Kind**: global class  
**Read only**: true  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| PERSPECTIVE | <code>string</code> | Perspective projection. |
| ORTHOGRAPHIC | <code>string</code> | Orthographic projection. |

<a name="new_CameraTypesEnum_new"></a>

### new CameraTypesEnum()
Enum for camera types.

<a name="DataTypesEnum"></a>

## DataTypesEnum
**Kind**: global class  
**Read only**: true  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| BOOLEAN | <code>string</code> | TRUE or FALSE. |
| INTEGER | <code>string</code> | Signed integer. |
| STRING | <code>string</code> | UTF8-encoded variable-length string. |
| FLOAT | <code>string</code> | Floating point number. |
| TIMESTAMP | <code>string</code> | W3C date and time formats. |

<a name="new_DataTypesEnum_new"></a>

### new DataTypesEnum()
Enum for SQL compatible data types.

<a name="EventsEnum"></a>

## EventsEnum
**Kind**: global class  
**Read only**: true  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| ON_MODEL_LOADED | <code>string</code> | . |
| ON_MODEL_PROGRESS | <code>string</code> | . |
| ON_MODEL_ERROR | <code>string</code> | . |
| ON_VIEWER_INITIALIZED | <code>string</code> | . |
| ON_VIEWER_STATUS_CHANGED | <code>string</code> | . |
| ON_VIEWER_ERROR | <code>string</code> | . |
| ON_SELECTION_CHANGED | <code>string</code> | . |
| ON_FULL_SCREEN_ENABLED | <code>string</code> | . |
| ON_FULL_SCREEN_DISABLED | <code>string</code> | . |
| FULL_SCREEN_UNSUPPORTED | <code>string</code> | . |

<a name="new_EventsEnum_new"></a>

### new EventsEnum()
Enum for events.

<a name="OperatorsEnum"></a>

## OperatorsEnum
**Kind**: global class  
**Read only**: true  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| EQUAL_TO | <code>string</code> | Equal to a value. Can be text, number or null. |
| NOT_EQUAL_TO | <code>string</code> | Not equal to a value. Can be text, number or null. |
| IN | <code>string</code> | Matches any value in a list of values. Can be text or number. |
| NOT_IN | <code>string</code> | Does not match any value in a list of values. Can be text or number. |
| STARTS_WITH | <code>string</code> | Starts with a text string. |
| DOES_NOT_START_WITH | <code>string</code> | Does not start with a text string. |
| ENDS_WITH | <code>string</code> | Ends with a text string. |
| DOES_NOT_END_WITH | <code>string</code> | Does not end with a text string. |
| CONTAINS | <code>string</code> | Contains a text string. |
| DOES_NOT_CONTAIN | <code>string</code> | Does not contain a text string. |
| GREATER_THAN | <code>string</code> | Greater than a numeric value. |
| GREATER_THAN_OR_EQUAL_TO | <code>string</code> | Greater than or equal to a numeric value. |
| LESS_THAN | <code>string</code> | Less than a numeric value. |
| LESS_THAN_OR_EQUAL_TO | <code>string</code> | Less than or equal to a numeric value. |
| BETWEEN | <code>string</code> | Between two numeric values. |

<a name="new_OperatorsEnum_new"></a>

### new OperatorsEnum()
Enum for comparison and pattern matching operators.

<a name="ViewerConfiguration"></a>

## ViewerConfiguration : <code>Object</code>
Configuation object used to initialise bimU.io Viewer.

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| domElementId | <code>string</code> | DIV element ID |
| showFPS | <code>boolean</code> | Whether show FPS meter. |
| showUI | <code>boolean</code> | Whether show UI. |
| buttonColor | <code>string</code> | CSS color keyword, RGBA, or Hex code for the default UI buttons. |

<a name="Viewpoint"></a>

## Viewpoint : <code>Object</code>
BCF-compatible viewpoint object.

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| camera | [<code>Camera</code>](#Camera) | Perspective camera or orthographic camera. |
| clippingPlanes | [<code>Array.&lt;ClippingPlane&gt;</code>](#ClippingPlane) | Clipping plane definition. |
| originatingSystem | <code>string</code> | Where this viewpoint was created from. |

<a name="Camera"></a>

## Camera : <code>Object</code>
BCF-compatible camera object.

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| cameraViewPoint | [<code>XYZ</code>](#XYZ) | Camera location. |
| cameraDirection | [<code>XYZ</code>](#XYZ) | Camera direction. |
| cameraUpVector | [<code>XYZ</code>](#XYZ) | Camera up vector. |
| fieldOfView | <code>number</code> | Camera’s field of view angle in degrees. |
| viewToWorldScale | <code>number</code> | Scaling from view to world. |

<a name="ClippingPlane"></a>

## ClippingPlane : <code>Object</code>
BCF-compatible clipping plane object.

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| normal | [<code>XYZ</code>](#XYZ) | The normal to the plane. |
| constant | <code>number</code> | The negative distance from the origin to the plane along the normal vector. |

<a name="XYZ"></a>

## XYZ : <code>Object</code>
BCF-compatible XYZ object.

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| x | <code>number</code> | X. |
| y | <code>number</code> | Y. |
| z | <code>number</code> | Z. |

<a name="TagOptions"></a>

## TagOptions : <code>Object</code>
Display options for Tag.

**Kind**: global typedef  
**Properties**

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| [shape] | <code>string</code> | <code>&quot;&#x27;circle&#x27;&quot;</code> | Use 'cicle' or 'rectangular'. |
| [fontName] | <code>string</code> | <code>&quot;&#x27;Helvetica&#x27;&quot;</code> | Font name. See https://www.cssfontstack.com/ for more details. FontAwesome is also |
| [fontSize] | <code>number</code> | <code>30</code> | Font size in pixel values (px). |
| [fontColor] | <code>string</code> | <code>&quot;&#x27;rgba(255, 255, 255, 1)&#x27;&quot;</code> | CSS color keyword, RBGA, or Hex code for text. |
| [backgroundColor] | <code>string</code> | <code>&quot;&#x27;rgba(97, 232, 240, 1)&#x27;&quot;</code> | CSS color keyword, RGBA, or Hex code for background. |
| [borderColor] | <code>string</code> | <code>&quot;&#x27;rgba(0, 0, 0, 0)&#x27;&quot;</code> | CSS color keyword, RGBA, or Hex code for border. Default is no border (transparent). |
| [borderThickness] | <code>number</code> | <code>0</code> | Border thickness in pixel values (px). |
| [visibleBehindObjects] | <code>boolean</code> | <code>true</code> | Whether tag is still visible when behind other objects. |
| [pulse] | <code>boolean</code> | <code>false</code> | Whether tag has pulse effect. |

