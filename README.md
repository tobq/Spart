# Spart

Dyamic version of [Shash](https://github.com/tobq/Shash)

### Setup
```javascript
var spart = new Spart(onNeighbour);
```
"gridItem" complient objects are added to the grid.

```javascript
spart.add(gridItem, width, height);

interface gridItem {
    coOrdinates coords;
}
interface coOrdinates {
    float x;
    float y;
}
```
### Running check

```javascript
spart.check()
``` 
This will check through the grid, and call the "onNeighbour" callback for each pair of neighbouring objects

```javascript
function onNeighbour(object1, object2){
    // Do work with neighbours, such as collision checking.
}
```
-----

Usage

You can include `<script src="https://raw.githubusercontent.com/tobq/Spart/master/Spart.js" async>` in a HTML file.

```javascript
// constructor
function rectangle(x, y, width, height){
    this.coords = {
        x: x || 0,
        y: y || 0
    };
    this.width = width || 10;
    this.height = height || 10
    spart.add(this, this.width, this.height);
}
function onNeighbour(object1, object2){
    console.log("NEIGHBOURS:", object1, object2);
}

var spart = new Spart(onNeighbour);
    
new rectangle(-10, 0);
new rectangle(-5, 0);
new rectangle(100, 50);
new rectangle(40, 200);
spart.check();
```
> **onNeighbour:** *NEIGHBOURS: rectangle {coords: {…}, width: 10, height: 10} rectangle {coords: {…}, width: 10, height: 10}*
