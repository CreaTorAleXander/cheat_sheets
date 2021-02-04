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

#### Promise All 
```
const promise1 = Promise.resolve(3);
const promise2 = 42;
const promise3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'foo');
});

Promise.all([promise1, promise2, promise3]).then((values) => {
  console.log(values);
});
// expected output: Array [3, 42, "foo"]

```

#### Make an Object Immutable
`Object.freeze(Obj)`
