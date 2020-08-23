# BIM Database

### Model Metadata
getFileProperties
getModelMetadata

``` javascript
// TODO
```

### Element Information
getElementDataByIndex

``` javascript
// TODO
```

### Database Query

``` javascript
let log = e => console.log(e);

let groupName1 = "Constraints";
let groupName2 = "Dimension";
let propertyName1 = "Top Constrant";
let propertyName2 = "Height";

let propertyFilter1 = new bimU.PropertyFilter(groupName1, propertyName1, "Level 1");
propertyFilter1.operator = bimU.OperatorsEnum.STARTS_WITH; // Default operator is equalTo.
let propertyFilter2 = new bimU.PropertyFilter(groupName2, propertyName2, 59.78);
propertyFilter2.operator = bimU.OperatorsEnum.GREATER_THAN;

let propertySelector1 = new bimU.PropertySelector(groupName1, "Top Offset");
propertySelector1.dataType = bimU.DataTypesEnum.FLOAT; // Default is STRING.
let propertySelector2 = new bimU.PropertySelector("Text", "Mark");
propertySelector2.alias = "Wall Mark";
```
getElementDataByProperty(propertyFilters, propertySelectors, limit, onSuccess, onError)

``` javascript
// SELECT "Constraints.Top Offset", "Text.Mark" as "Wall Mark"
// FROM (bimU Cloud BIM Database)
// WHERE "Constraints.Top Constrant" LIKE "Typical Level: %" AND "Dimension.Height" > 59.78
// LIMIT 100
let propertyFilters = [propertyFilter1, propertyFilter2]; // Properties to search. All conditions must satisfy (AND - intersection).
let propertySelectors = [propertySelector1, propertySelector2]; // Properties to return. Maximum 5.
let limit = 100; // Return only first 100 elements
viewer.getElementDataByProperty(propertyFilters, propertySelectors, limit, log, log);
```

getElementDataByQuery(filterExpression, selectExpression, limit, onSuccess, onError)

``` javascript
// Text.Mark is "W-001-A"
let selectExpression = 'CAST("Constraints.Top Offset" AS FLOAT), SUBSTRING("Text.Mark", 2, 3) as "Wall Mark"';
let filterExpression = '"Constraints.Top Constrant" LIKE "Typical Level: %" AND CAST("Dimension.Height" AS FLOAT) > 59.78'; 
viewer.getElementDataByQuery(filterExpression, selectExpression, limit, log, log);
```
quantity/metric
aggregateElementProperty(propertyFilters, propertyToAggregate, aggregateFunction, onSuccess, onError)

``` javascript
// Aggregate functions: avg, sum, count, max, min, etc...
let func = bimU.AggregateFunctionsEnum.AVG;
viewer.aggregateElementProperty(propertyFilters, propertySelector1, func, log, log);
```