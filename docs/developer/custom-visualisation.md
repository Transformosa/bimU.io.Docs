# Custom Visualisation

### Tagging
addTag(text, location, options, onClick)
removeTag

``` javascript
// Available tag options
let tagOptions = {
    shape: 'circle',
    fontName: 'Helvetica',
    fontSize: 20,
    fontColor: { r: 160, g: 32, b: 21, a: 1.0 },
    backgroundColor: { r: 97, g: 232, b: 240, a: 1.0 },
    borderColor: { r: 160, g: 32, b: 21, a: 1.0 },
    borderThickness: 5,
    visibleBehindObjects: true,
    pulse: true,
};

// Default
viewer.addTag("A", new THREE.Vector3(0, 0, 0));
// Circle
viewer.addTag("B", new THREE.Vector3(0, 0, 3), {shape: 'rectangular'});
// Font
viewer.addTag("C", new THREE.Vector3(1.5, 0, 0), {fontName: 'Times New Roman', fontSize: 200, fontColor: { r: 244, g: 255, b: 129, a: 1.0 }});
// Border
viewer.addTag("D", new THREE.Vector3(1.5, 0, 3), {borderThickness: 30, borderColor: { r: 244, g: 255, b: 129, a: 1.0 }});
// Background
viewer.addTag("E", new THREE.Vector3(1.5, 0, 1.5), {backgroundColor: { r: 230, g: 81, b: 0, a: 1.0 }});
// Empty Text
viewer.addTag(" ", new THREE.Vector3(3, 0, 0), {fontSize: 100});
// Long Text
viewer.addTag("Hello World", new THREE.Vector3(3, 0, 3), {shape: 'rectangular'});
```

### Custom Objects
addObject
removeObject
zoomToObject(object3D)

``` javascript
// TODO: add a cylinder and a cube
viewer.addObject(object);
```
