# Composition

```js
function compose(...pipe) {
  return function(arg) {
    return pipe.reduce(function(prev, fn, index) {
      return index == 1 ? fn(prev(arg)) : fn(prev);
    });
  }
}

function around100(arg) {
  return arg.filter(function(item) {
    return (90 < item && item < 110);
  });
}

function square(arg) {
  return arg.map(function(item) {
    return item * item;
  });
}

function sum(arg) {
  return arg.reduce(function(acc, item) {
    return acc + item;
  });
}

function average(arg) {
  var count = arg.length,
      sum = arg.reduce(function(item, acc) {
    return item + acc;
  });
  return sum / count;
}

var arr = [0, 1, 2, 90, 95, 100, 109, 120];

var r1 = sum( square( around100( arr ) ) ); // Manual composition

var fn = compose(around100, square, sum); // Compose new function
var r2 = fn( arr );

var fn1 = compose(around100, square, average);
var r3 = fn1( arr );
```
