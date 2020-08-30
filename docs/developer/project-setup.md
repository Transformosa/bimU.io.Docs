# Project Setup

### Dependencies
bimU.io Viewer API is based on Three.js. So the both libraries must be included in your project. Additionally, Three.js must be loaded in global scope and exposed as a global variable called THREE.

If you use vanilla HTML, CSS, JavaScript or a front-end framework that doesn't require compilation, such as Bootstrap, Semantic UI, etc., both Three.js and bimU.io Viewer API are exported as Universal Modules that can be included before your project's closing ```</body>``` tag. For example, the both libraries are available over a CDN:

``` html
<script src="https://cdn.jsdelivr.net/npm/three@0.113.2/build/three.min.js" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bimu.io.viewer@0.0.6/dist/bimU.io.Viewer.umd.js" crossorigin="anonymous"></script>
```

You can also use a JavaScript package manager to install the both libraries. Since Three.js is specified as a dependency of bimU.io Viewer API, below is an NPM command that will save them to your project folder at the same time.

```
npm install bimu.io.viewer --save
```

If you use a front-end framework that requires a module loader or a compilation step, such as React, Angular, Vue, etc., please make sure Three.js is loaded first and accessible by a global variable called ```THREE``` **before** importing bimU.io's ES6 module. The type definitions are included in the package, so you can also benefit from the IntelliSense in Visual Studio Code.

``` javascript
// ThreeImporter.js
import * as THREE from 'three/build/three';
// Assign THREE to global variable
window.THREE = THREE;
```

``` javascript
// ViewerComponent.js
import ThreeImporter from './ThreeImporter';
import * as bimU from 'bimu.io.viewer';
```

### Debugging
All available bimU.io Viewer API functions are exposed as methods of the ```Viewer``` object. It would be easier to explore and inspect in browser console if a ```viewer``` variable is also exposed in global scope.

``` javascript
let viewer = new bimU.Viewer(viewerConfigs);
viewer.initialize();
window.viewer = viewer;
```

### Sample Projects
We've created a couple of Hello World boilerplates:

- [Vanilla HTML + JavaScript Sample Project](https://github.com/bimU-io/VanillaSample): This project loads a model on a dummy HTML web page with some basic UI.

- [React Sample Project](https://github.com/bimU-io/ReactSample): This project is a React.js web application set up by using [Create React App](https://create-react-app.dev/).