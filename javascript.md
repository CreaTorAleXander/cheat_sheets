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

#### How to use reduce 
```
const result = Object.values(products).reduce((a, c) => {
    for (const key in c) {
    // entweder der Wert oder neues Array
       a[key] = a[key] || [];
       a[key].push(c[key]);
    }
    return a;
},{});
```
