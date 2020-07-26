# User Interface

### Default Toolbar
toggleFullscreen
readCoordinates
measureDistance
measureHeight
measureAngle
measureArea
clearAllMeasurements

### Custom Button
addCustomButton(domElementId, icon, color, tooltip, callback)
removeDomElement

``` javascript
viewer.addCustomButton("button1", "wifi", "#2196F3", "Like it", function(){ alert("You liked this model."); });
viewer.addCustomButton("button2", "router", "#4CAF50 ", "Unlike it", function(){ alert("You unliked this model."); });
```

### Dialog
showDialog
closeDialog
showHelp
showElementInformation

### Miscellaneous
setBackgroundColor
toggleWireframeMode
