# Square of hipotenuse

## 1. Iterative

  ```js
  // JavaScript
  const squareOfHipotenuse = function(a, b) {
  return a * a + b * b;
}

squareOfHipotenuse( 3, 4 );
```

```Scheme
; Scheme
(define (square-of-hipotenuse a b) 
  (+ (* a a) (* b b)))
  
  (square-of-hipotenuse 3 4)
  ```
## 2. Decomposition of first level (abstraction of square)

```js
// JavaScript
const square = function(x) {
  return x * x;
}

square(3);
```

```js
// JavaScript
const square = function(x) {
  return x * x;
}

const squareOfHipotenuse = function(a, b) {
  return square(a) + square(b);
}

squareOfHipotenuse( 3, 4 );
```

```Scheme
; Scheme
(define (square x) 
  (* x x))
  
 (square 3)
 ```
 ```Scheme
 ; Scheme
 (define (square x) 
  (* x x))

(define (square-of-hipotenuse a b) 
  (+ (square a) (square b)))

(square-of-hipotenuse 3 4)
```

## 3. Area of a circle

```Scheme
(define (square x) (* x x))

(define pi 3.1415)

(define (area-of-circle r) (* pi (square r)))

(area-of-circle 10)
```

## 4. Decomposition of second level (abstraction of power)

```Scheme
; Scheme
(define (** x pow) 
  (cond ((> pow 1) (* x (** x (- pow 1))))
        ((= pow 1) x)
        (else 0)))
 (** 2 8)
 ```
 
 ```Scheme
 ; Scheme
 (define (** x pow) 
  (cond ((> pow 1) (* x (** x (- pow 1))))
        ((= pow 1) x)
        (else 0)))
        
 (define (square x) 
  (** x 2))

(square 3)
```

```Scheme
; Scheme
(define (** x pow) 
  (cond ((> pow 1) (* x (** x (- pow 1))))
        ((= pow 1) x)
        (else 0)))
      
(define (square x) 
  (** x 2))

(define (square-of-hipotenuse a b) 
  (+ (square a) (square b)))

(square-of-hipotenuse 3 4)
```
