## Like 
- let str = JSON.stringify(obj, null, 4); // Debugging Display Object Beautiful Indended
- JSON.parse(str); // revert this above


## Arrays
#### Join 
```
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// expected output: "Fire,Air,Water"

console.log(elements.join(''));
// expected output: "FireAirWater"

console.log(elements.join('-'));
// expected output: "Fire-Air-Water"
```
