# Event Handling

### Event Types

### Event Registration

``` javascript
let onLoaded = (e) => console.log(e);
viewer.addEventListener(bimU.EventsEnum.ON_VIEWER_INITIALIZED, onLoaded);
```

### Callback and Event Arguments

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