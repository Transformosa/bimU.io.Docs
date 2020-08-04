# Event Handling

### Event Types
You can subscribe to a particular event when it is triggered by bimU.io Viewer API or user behaviours. For example, a subscription to the ```ON_MODEL_PROGRESS``` event reports model loading progress. An animated progress bar can then be displayed on your user interface within an event handler function. All available events can be found under the ```bimU.EventsEnum``` object.

### Event Subscription
bimU.io Viewer API takes advantage of the ```EventDispatcher``` supported by Three.js. ```addEventListener``` is a method of the ```Viewer``` class. Below is an example showing how to subscribe to the ```ON_VIEWER_INITIALIZED``` event by passing an event type and an event handler into the ```addEventListener``` function. 

``` javascript
let onLoaded = (e) => console.log(e);
viewer.addEventListener(bimU.EventsEnum.ON_VIEWER_INITIALIZED, onLoaded);
```

For some events, an event handler won't work if subscription is done after it happens. For example, you must subscribe to the ```ON_VIEWER_INITIALIZED``` event and the ```ON_MODEL_PROGRESS``` event prior to calling the ```initialize``` function and the ```loadModel``` function respectively.

### Event Handler and Event Argument
An event handler is simply a callback function that takes an event argument. All information related to an event can be found from the properties of the event argument object. The best way to inspect an event arugment is logging it out. Below is an example responding to a UI event when a model element is clicked by user. Clicking on a model element can either select or deselect it. If it is selected, a further action can be taken in the callback function.

``` javascript
viewer.addEventListener(bimU.EventsEnum.ON_SELECTION_CHANGED, (e) => {
    console.log(e);
    //{
    //    clickedElementIndex: 2,
    //    isClickedElementSelected: true,
    //    selectedElementIndices: [0, 1, 2],
    //    type: "onSelectionChanged"
    //}

    if(e.isClickedElementSelected){
        viewer.getElementDataByIndex(e.clickedElementIndex, onLoaded, onError);
    }
});
```