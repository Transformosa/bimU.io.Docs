# Navigation Controls

### Basics
There are a few built-in functions that adjust the viewer camera to focus on particular angles or items, such as ```alignToView```, ```zoomToFit```, ```zoomToSelection```, ```zoomToObject```, etc. These functions are also available on the default user interface.

### Camera Viewpoint
Tweaking camera parameters can be a complicated task. bimU.io adopts the prevailling [BCF (BIM Collaboration Format)](https://github.com/buildingSMART/BCF-XML/tree/release_2_1/Documentation#visualization-information-bcfv-file) open standard and simplifies its data schema to streamline this process. To capture current camera viewpoint in the viewer, calling the ```getViewpoint``` function returns the following JSON format. You can keep it somewhere (e.g., in your own database) and pass it into the ```setViewpoint``` function later on to restore a previously saved viewpoint. Note that element information is not stored in the JSON object at the moment.

``` json
{
  "camera": {
    "cameraViewPoint": {
      "x": -0.9173076695143414,
      "y": -2.981698504183087,
      "z": 23.5427893532144
    },
    "cameraDirection": {
      "x": 0.23320190941814167,
      "y": 0.48592126302799127,
      "z": -0.8423166836653626
    },
    "cameraUpVector": {
      "x": 0.3644454140253172,
      "y": 0.7593924780881949,
      "z": 0.538982935183467
    },
    "viewToWorldScale": 0,
    "fieldOfView": 60
  },
  "originatingSystem": "bimU.io Web Viewer"
}
```

### Sectioning
Section plane/clipping plane information can be captured in the BCF-compatible JSON format as well. Below is a sample camera viewpoint when section box is enabled in the viewer.

``` json
{
  "camera": {...},
  "clippingPlanes": [
    {
      "normal": {"x": -1, "y": 0, "z": 0},
      "constant": -15.612010478973389
    },
    {
      "normal": {"x": 1, "y": 0, "z": 0},
      "constant": -27.28821611404419
    },
    {
      "normal": {"x": 0, "y": -1, "z": 0},
      "constant": -3.803048580420051
    },
    {
      "normal": {"x": 0, "y": 1, "z": 0},
      "constant": -9.255849331152472
    },
    {
      "normal": {"x": 0, "y": 0, "z": -1},
      "constant": -6.7235229899076785
    },
    {
      "normal": {"x": 0, "y": 0, "z": 1},
      "constant": -17.06601223246139
    }
  ]
}
```

It's worth to know that section box visibility and section planes applied in the JSON object are separate things. Section box is a built-in functionality in the user interface. Call the ```toggleSectionbox``` function to make it visible or hidden. To control the extents of section box, you can take advantage of the ```setSectionBox``` and the ```sectionAroundSelection``` functions. Call the ```resetVisibility``` function to clear current section box state.

### Camera Projection
bimU.io Viewer uses perspective camera by default which is the most common projection mode for rendering a 3D scene. If you wish to switch to orthographic projection, call the ```setProjectionMode``` function and use the ```isPerspectiveMode``` function to check current projection mode.

If current viewpoint is rendered by perspective camera, the ```fieldOfView``` property in the BCF-compatible JSON object is a positive value. Otherwise, the ```viewToWorldScale``` will be a positive value when orthographic camera is used.
