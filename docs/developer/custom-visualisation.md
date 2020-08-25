# Custom Visualisation

### Tagging
A tag is an overlay marker or label that identifies a location in 3D scene. You can use it to create annotations for a model. The ```addTag``` function returns a UUID that can be used to remove a tag from the viewer later on.

``` javascript
// Create a tag showing a number 1.
let uuid = viewer.addTag("1", new THREE.Vector3(0, 0, 0));
// Remove a tag by its UUID
viewer.removeTag(uuid);
```

There are various different options to configure how a tag looks like:

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
viewer.addTag("A", new THREE.Vector3(0, 0, 0), tagOptions);
// Default
viewer.addTag("B", new THREE.Vector3(0, 0, 0));
// Circle
viewer.addTag("C", new THREE.Vector3(0, 0, 3), {shape: 'rectangular'});
// Font
viewer.addTag("D", new THREE.Vector3(1.5, 0, 0), {fontName: 'Times New Roman', fontSize: 200, fontColor: { r: 244, g: 255, b: 129, a: 1.0 }});
// Border
viewer.addTag("E", new THREE.Vector3(1.5, 0, 3), {borderThickness: 30, borderColor: { r: 244, g: 255, b: 129, a: 1.0 }});
// Background
viewer.addTag("F", new THREE.Vector3(1.5, 0, 1.5), {backgroundColor: { r: 230, g: 81, b: 0, a: 1.0 }});
// Empty Text
viewer.addTag(" ", new THREE.Vector3(3, 0, 0), {fontSize: 100});
// Long Text
viewer.addTag("Hello World", new THREE.Vector3(3, 0, 3), {shape: 'rectangular'});
```

### Custom Object
Any Three.js ```Object3D``` object can be added to the viewer via the ```addObject``` function. You can take advantage of the existing loaders provided by [Three.js Examples](https://threejs.org/examples/?q=loader) to import a generic 3D object, such as furniture, analytical model, etc. The ```zoomToObject``` function is able to nagivate user to where a 3D object is placed. To remove a 3D object from the viwer, simply pass its UUID to the ```removeObject``` function. See an example below. 

``` javascript
// Create a cylinder object
let geometry = new THREE.CylinderGeometry(5, 5, 20, 32);
let material = new THREE.MeshBasicMaterial({color: 0xffff00});
let cylinder = new THREE.Mesh(geometry, material);
// Move to somewhere visible
cylinder.position.set(10, 20, 30);
// Keep the returned UUID
let uuid = viewer.addObject(cylinder);
// Then it can be removed later
viewer.removeObject(uuid);
```
