# Getting Started with bimU.io Viewer API

Advanced users, digital specialists, and software developers can take advantage of bimU.io Viewer API (Application Programming Interface) to create bespoke BIM Web applications based on the bimU.io platform technology. We aim to make your development experience simple and allow you to quickly put together BIM applications on the Web without having to handle 3D computer graphics from scratch.

### Overview
bimU.io Viewer API is a development toolkit that provides out-of-the-box 3D BIM viewer and database. It is packaged as a web front-end library that is able to:
- render BIM models hosted on bimU.io in your own web application.
- extend bimU.io Viewer's core functionality.
- retrieve model and element information from BIM database.
- create BIM-based digital solutions, such as custom visualisation, data analytics, Digital Twin, IoT (Internet of Things), etc.

### Prerequisites
- Basic programming skills and web development experience in JavaScript, HTML, CSS, etc. will be helpful. bimU.io Viewer is built upon the most popular Web 3D library - Three.js. Knowledge in computer graphics and Three.js will bring you up to speed.
- You need to have a bimU.io Pro account which is currently the default subscription and freely available until December 2020.
- You need to upload your BIM model to bimU.io Viewer or simply use the sample models provided by bimU.io.
- There are various different options in terms of website hosting. For development purpose, we recommend Web Server for Chrome if you are going to code in vanilla HTML, JavaScript, or jQuery. Furthermore, if you are an experienced web developer, a development server included in a front-end stack or boilerplate, such as React, Angular, Vue, etc. is a preferred option. For production use, while most cloud providers, such as AWS, Azure, etc. offer static site hosting capabilities, products like Netlify or Firebase Hosting would make your life much easier.
- Using the latest version of Google Chrome browser is always recommended.

### Main Concepts
- When a BIM model is loaded via bimU.io Viewer JavaScript API, it literally has the same functionality as in bimU.io Viewer. You can further customise how the viewer component or your model looks like by calling other API methods.
- After proper initialisation, the viewer component can render a bimU.io-hosted model on your own webpage if correct crednetials are provided. Your website will then manipulate the viewer component and the loaded model with bimU.io Viewer JavaScript API.
- The viewer component is a pure front-end, browser-side 3D canvas based on WebGL technology. You don't necessarily have to set up a back-end server application if password authentication is used. However, it is strongly recommended to use API Key authentication which requires a back-end, server-side web application to request for a one-time access token to load a model.
- The viewer component will load full geometry initially for users to see entire model visually. However, it does not load all non-geometric BIM data at once. There are several API methods that can query server-side BIM database to retrieve model metadata, element properties, etc. individually.

### Quick Start
We've put together a JSFiddle to walk you through a quick demo with minimum setup to load a sample bimU.io model. With all necessary dependencies added in, you can easily start to play around bimU.io Viewer API in the sandbox by opening or cloning the JSFiddle here.

Below is a <div> element that functions as a container for the viewer component. A DOM ID must be specified and passed into a viewer configuration object for initialisation.
``` html
<div id="viewer" style="width:1000px;height:500px;background-color: black;border: 5px solid black;"></div>
```

Firstly, a Viewer object must be initialised with proper configuration. A model can then be loaded by supplying model configuration and callback functions to the loadModel method. The methods exposed by the Viewer object provide all functionality.
``` javascript
let onPorgress = (e) => console.log(e); // Callback that reports model loading progress.
let onLoaded = (e) => console.log(e); // Callback when model is fully loaded.
let onError = (e) => console.log(e); // Callback when model fails to load.

// Viewer configuration object
let viewerConfigs = {
    domElementId: "viewer",
    showUI: true
};

// Initialise a Viewer 
let viewer = new bimU.Viewer(viewerConfigs);
viewer.initialize();

// Model configuration object
let modelConfigs = {
    modelId: "5e545747597b680004e70414",
    password: ""
};

// Load a model
viewer.loadModel(modelConfigs, onPorgress, onLoaded, onError);
```

### Support
Please log a ticket on bimU.io's support centre or email support@bimu.io if you have any query. bimU.io Support Team is more than happy to answer any technical questions.