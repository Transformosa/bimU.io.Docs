# Navigation Controls

### Basics
alignToView
zoomToFit
zoomToSelection
zoomToObject(object3D)

### Camera Viewpoint
[https://github.com/buildingSMART/BCF-XML/tree/release_2_1/Documentation#visualization-information-bcfv-file|BCF Documentation]
getViewpoint
setViewpoint
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
Section box visibility and section planes are separate things.
toggleSectionbox
sectionAroundSelection
isPointInSectionBox
setSectionBox
setViewpoint
resetVisibility

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

### Camera Projection
isPerspectiveMode
setProjectionMode