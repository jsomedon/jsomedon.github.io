Function objects in js have a property called `prototype`. If you make new object, the constructor's `prototype` property becomes prototype of new object.

```
var f = function () {};
f.prototype;
var obj = new f(); 
obj.__proto__ === f.prototype;
```

You add new properties to prototype and your objects see that too.

```
var a = new f();
a.x; // undefined, f.prototype doesn't have x as property yet
f.prototype.x = 1; // adding x
a.x; // 1
```

You add new property to an object then the object's prototype won't notice that.

```
a.y; // undefined
a.y = 2;
a.y; // now 2
f.prototype.y; // undefined
```

You change constructor's `prototype` property. Objects created before this change would still remember the old prototype. Only objects created after this change will have that new prototype.

```
f.prototype = {z:3}; // before it was {x:1}
// b's prototype is the new {z:3}
var b = new f();
b.x; // undefined
b.z; // 3
// a's prototyp is still {x:1}
a.x; // 1
a.z; // undefined
```

`Object.create()` creates prototypical relation.

```
var obj = Object.create(proto); // now obj's prototype is proto
```

We used to have noway whatsoever to access an object's prototype by the standard, until ES6.

```
obj.__proto__; // this actually kinda worked before ES6 but that was a vendor implemented feature
```

Side note: in a method call, `this` always point to invoking object.
```
f.prototype.aMethod = function () { /* some code using this */ };
a.aMethod(); // here, this points to a not f.prototype
```
Maybe I should write about `this` in detail another day.
