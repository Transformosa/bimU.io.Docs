# BIM Database
bimU.io is not only a BIM model viewer but also a full-fledged, cloud-hosted database where BIM data is readily available. Once a BIM model is uploaded to bimU.io and processed succesfully, every element property can be individually retrieved, filtered, transformed, aggregated upon a SQL-compliant query. Make sure a model is fully loaded in the viewer component before requesting for data or sending a database query. The ```ON_MODEL_LOADED``` event can be of use.

### Model Metadata
There are two model-level data functions: ```getFileProperties``` and ```getModelMetadata```. The former returns bimU.io's system properties of a model file, such as author, timestamp, source, etc. The latter returns model-level information contained in a BIM model, such as parameters in Revit Project Information.

``` javascript
const onSuccess = (data) => console.log(data);
const onError = (errorMessage) => console.error(errorMessage);
viewer.getFileProperties(onSuccess, onError);
viewer.getModelMetadata(onSuccess, onError);
```

### Element Data
The ```getElementDataByIndex``` function returns all element properties for a specified element index. Every element property has a property group that categorises relevant properties. Below example shows how to get properties for a selected model element.

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
        viewer.getElementDataByIndex(e.clickedElementIndex, onSuccess, onError);
    }
});
```

### Database Query

#### Filtering and Projection
It is vitally important to narrow down search conditions in order to build an efficient query. A couple of wrapper classes come into play for filtering and projecting existing properties of model elements. A ```PropertyFilter``` object filters out model elements that match the specified condition. Various operators are available in the ```OperatorsEnum``` that can be assigned to a property filer. Additionally, as it is too cumbersome to retrieve all the properties in one go, a ```PropertySelector``` must be used to return only the specified property. In essence, a property filer limits the number of model elements returned, while a property selector limits the number of element properties returned. A comprehensive example is provided below.

``` javascript
let groupName1 = "Constraints";
let groupName2 = "Dimension";
let propertyName1 = "Top Constrant";
let propertyName2 = "Height";

// Filter out elements that have a property called "Top Constrant" in a "Constraints" group and its value starts with "Typical-Floor-".
let propertyFilter1 = new bimU.PropertyFilter(groupName1, propertyName1, "Typical-Floor-");
// Default operator is EQUAL_TO.
propertyFilter1.operator = bimU.OperatorsEnum.STARTS_WITH;
// Filter out elements that have a property called "Height" in a "Dimension" group and its value is greater than 12.34.
let propertyFilter2 = new bimU.PropertyFilter(groupName2, propertyName2, 12.34);
propertyFilter2.operator = bimU.OperatorsEnum.GREATER_THAN;

// Return a property called "Top Offset" in a "Constraints" group.
let propertySelector1 = new bimU.PropertySelector(groupName1, "Top Offset");
// Convert STRING to FLOAT. Default data type is STRING.
propertySelector1.dataType = bimU.DataTypesEnum.FLOAT;
// Return a property called "Mark" in a "Text" group.
let propertySelector2 = new bimU.PropertySelector("Text", "Mark");
// Rename the property name to "Wall Mark" when data is returned.
propertySelector2.alias = "Wall Mark";
```

A corresponding SQL query should look like this:

``` sql
SELECT "Constraints:Top Offset", "Text:Mark" as "Wall Mark"
FROM (bimU Cloud BIM Database)
WHERE "Constraints:Top Constrant" LIKE "Typical-Floor-%" AND "Dimension:Height" > 12.34
LIMIT 100
```

#### Query Builder
When property filters and property selectors are created, they should then be put together in two separate arrays to build a query. Call the ```getElementDataByProperty``` function to execute a query like below.

``` javascript
// Properties to search. All conditions must satisfy (AND - intersection).
let propertyFilters = [propertyFilter1, propertyFilter2];
// Properties to return. Up to 5 properties can be returned.
let propertySelectors = [propertySelector1, propertySelector2];
// Return only the first 100 model elements that match the conditions.
let limit = 100;
viewer.getElementDataByProperty(propertyFilters, propertySelectors, limit, onSuccess, onError);
```

#### Model Element Identifiers
As mentioned [here](/developer/model-elements), bimU.io uses **element index** as model element identifier internally. In addition to that, bimU.io also stores other identifiers sourced from authoring formats. Every identifier has a corresponding property name stored in the BIM database as well:

- ```eIdx```: bimU.io's internal element index.
- ```uId```: Unique ID, such as IFC's ```IfcGuid```, Revit's ```UniqueId```, Navisworks' ```InstanceGuid```, and Tekla's ```Identifier.GUID```.
- ```eId```: Element ID, such as Revit's ```ElementId``` and Tekla's ```Identifier.ID```.

To use identifiers in a database query, simply leave **group name** blank or ```null```:

``` javascript
// Look for element index equals to "0"
let propertyFilter1 = new bimU.PropertyFilter(null, "eIdx", "0");
// Return unique ID
let propertySelector1 = new bimU.PropertySelector("", "uId");
// Return element ID as integer and rename it to "ElementId"
let selectExpression = `CAST("eId" AS INTEGER) as "ElementId"`;
```

#### Raw Query
It is possible to create a very complicated query. That said, writing an arbitrary query from scratch is only recommended for advanced users. If you have good knowledge in SQL, you can write a **Filter** expressesion along with a **Select** expression to run the ```getElementDataByQuery``` function like below.

``` javascript
// "Text:Mark" is "W-001-A" for example. Here we want to extract the three numbers in between.
let selectExpression = `CAST("Constraints:Top Offset" AS FLOAT), SUBSTRING("Text:Mark", 2, 3) as "Wall Mark"`;
let filterExpression = `"Constraints:Top Constrant" LIKE 'Typical-Floor-%' AND CAST("Dimension:Height" AS FLOAT) > 59.78`; 
viewer.getElementDataByQuery(filterExpression, selectExpression, limit, onSuccess, onError);
```

Some useful tips for writing a query:

- Column name is composed of a group name and a property name with a colon ``` : ``` as a delimiter in between.
- Column name should be wrapped in double quotes ``` " ```. String value should be wrapped in single quotes ``` ' ```. To avoid using escape characters, [JavaScript Template Literal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) ``` ` ``` is the best way to create an expression string.
- Note that all input data is treated as a string. It must be cast into the relevant data types when necessary.

#### Aggregation
Aggregation query is also supported. To calculate a quantity or create a metric, call the ```aggregateElementProperty``` function to summarise values of a single element property. For example, to get the average "Top Offset" value of the model elements matching the filtering conditions:

``` javascript
// Aggregate functions: avg, sum, count, max, min, etc...
let func = bimU.AggregateFunctionsEnum.AVG;
viewer.aggregateElementProperty(propertyFilters, propertySelector1, func, onSuccess, onError);
```

#### Limitation

- **Number of Properties:** Maximum of 5 properties can be returned in one single query.
- **Query Timeout:** 2 seconds. HTTP response status code 408 if it takes too long.
- **Query Data Size:** 1 MB. HTTP response status code 413 if response payload is too large.
- **Supported Data Types:** bool, int, integer, string, float, decimal, numeric, timestamp.
- **Supported Operators:**

|                            |                                      |
|----------------------------|--------------------------------------|
| Logical Operators          | AND, NOT, OR                         |
| Comparison Operators       | <, >, <=, >=, =, <>, !=, BETWEEN, IN |
| Pattern Matching Operators | LIKE, _, %                           |
| Unitary Operators          | IS NULL, IS NOT NULL                 |
| Math Operators             | +, -, *, /, %                        |

- **Supported Functions:**

|                       |                                                               |
|-----------------------|---------------------------------------------------------------|
| Conversion Functions  | CAST                                                          |
| Conditional Functions | CASE, COALESCE, NULLIF                                        |
| Date Functions        | DATE_ADD, DATE_DIFF, EXTRACT, TO_STRING, TO_TIMESTAMP, UTCNOW |
| String Functions      | CHAR_LENGTH, CHARACTER_LENGTH, LOWER, SUBSTRING, TRIM, UPPER  |
| Aggregate Functions   | AVG, COUNT, MIN, MAX, SUM                                     |