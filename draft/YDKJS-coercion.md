# abstract method

## toString()

```
null      // "null"
undefined // "undefined"
true      // "true"
number    // "<number>" || "<exponent form>"
object    // object.toString() || [object Object]
array     // "[a,b,c]"
```

## JSON.stringify()

### mostly same as toString(), but always a string:

```
"42" // ""42"" -- quote preserved
```

### illegal JSON value

the rules:
```
// skip (return undefined), or return null if in array, skip serializing if it's an object property
undefined
function
symbol
// throw error
object with circular ref
```

to legalize:
- define illegal-json-obj.toJSON() to return legal JSON value
- stringify() will call on toJSON()'s value automatically

## toNumber()

```
true // 1
false // 0
undefined // NaN
null // 0
string // number || NaN
object // toPrimitive().toNumber()
// toPrimitive() -> valueOf() and it should be primitive value || toString() || TypeError
```

## toBoolean

### falsy
```
undefined
null
false
+0 -0 NaN
""
//... and other stuff like document.all in modern ie
```

### truthy
everything else..

# explicit coercion

## the most explicit three
```
// dont use new! just use them as function!
Number()
String()
Boolean()
```

## to string
```
// if value is primitive, box it first
value.toString()
```

## to number
```
// most people understand this
+value
```

## Date to number
```
+dateValue
dateValue.getTime()
Date.now() // same as +new Date()
```

## bitwise
```
// bitwise ops coerce operands to 32 bits number
// -0, NaN, Infinity, -Infinity are 64 bits
// and become 0 on coercion
0 | Infinity -> 0
// ~ is bitwise not
// roughly ~x = -(x+1)
~-1 -> 0 // falsy
~other numbers -> non-0 // truthy
```

## parse number vs to number
Number() is strict but parseInt() is tolerant:
```
Number(   "42aaa" );	// NaN
parseInt( "42aaa" );	// 42
```
for pre-ES5, specify base: parseInt(string, base)  
for post-ES5, decimal as default

## to bool
```
!!value
```

# implicit coercion
## string -> number
