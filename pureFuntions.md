# Pure Functions


A pure function has two characteristics:
- **No Side Effects**: A pure function has no effect on the program or the world besides outputting its return value 
- **Deterministic**: Given the same input values, a pure function will always return the same output. This is because its return value depends only on its input parameters, and not on any other information (e.g. global program state)


## Pure or not?

Decide whether each of the following functions is pure or impure, and why. Use the characteristics described above to decide.



```javascript
getDate = ƒ()

function getDate() {
  return new Date().toDateString();
}
```
🙌 getDate is Not Pure

Explanation
A function is not pure if its output depends on anything except its inputs (including the state of the world), or if calling the function at different times with the same inputs can give different outputs (e.g. if called on different days).





```javascript
getWorkshopDate = ƒ()

function getWorkshopDate () {
  return new Date(2020, 11, 4).toDateString();
}
```
🙌 getWorkshopDate is Pure

Explanation
A function is pure if its output depends on nothing but its inputs, and it always returns the same output if called with the same inputs (in this case, no inputs).





```javascript
toHex = ƒ(n)

function toHex(n) {
  let hex = n.toString(16);
  return hex.padStart(2, '0');
}
```

🙌 toHex is Pure

Explanation
A function is pure if its output depends on nothing but its inputs, it does nothing except return its output, and it always returns the same output if called with the same input.





```javascript
rgbToHex = ƒ(R, G, B)

function rgbToHex(R, G, B) {
  return '#' + [toHex(R), toHex(G), toHex(B)].join('');
}
```

🤔 rgbToHex is Pure

Explanation
A function is pure if its output depends on nothing but its inputs, it does nothing except return its output, and it always returns the same output if called with the same input.






```javascript
setColor = ƒ(R, G, B)

function setColor(R, G, B) {
  const hex = rgbToHex(R, G, B);
  const colorMe = document.getElementById('color-me');
  colorMe.setAttribute('style', 'color: ' + hex);
}
```

Explanation
A function is not pure if it does anything besides return its output. Any other effect it has on the program or world is a side effect (in this case, changing the properties of an HTML element on the page).






```javascript
readJsonFile = async ƒ(filename)

async function readJsonFile(filename) {
  const file = await fetch(
    'https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_hour.geojson'
  );
  return await file.json();
}
```

🙌 readJsonFile is Not Pure

Explanation
A function is not pure if its output depends on the state of the world (in this case, the contents of web-hosted file), or if calling the function at different times with the same inputs can give different outputs.





```javascript
writeJsonString = ƒ(object)

function writeJsonString(object) {
  return JSON.stringify(object, null, 2);
}
```
🙌 writeJsonString is Pure

Explanation
A function is pure if its output depends on nothing but its inputs, and it always returns the same output if called with the same input. In this case, calling it on the same object will always return the same string.






```javascript
exclusiveOr = ƒ(A, B)

function exclusiveOr(A, B) {
  return (A || B) && !(A && B);
}
```
🙌 exclusiveOr is Pure

Explanation
A function is pure if its output depends on nothing but its inputs, it does nothing except return its output, and it always returns the same output if called with the same input.





```javascript
computeTruthTable = ƒ(operator)

function computeTruthTable(operator) {
  const truthValues = [true, false];
  const table = [];
  for (const A of truthValues) {
    for (const B of truthValues) {
      const value = operator(A, B);
      table.push({ A, B, value });
    }
  }
  return table;
}
```
🙌 computeTruthTable is Pure

Explanation
A function is pure if its output depends on nothing but its inputs, it does nothing except return its output, and it always returns the same output if called with the same input.




```javascript
showTruthTable = ƒ(operator)

function showTruthTable(operator) {
  console.table(computeTruthTable(operator));
}
```
🙌 showTruthTable is Not Pure

Explanation
A function is not pure if it does anything besides return its output. Any other effect it has on the program or world is a side effect (in this case, logging information to the console).