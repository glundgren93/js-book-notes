## Chapter 2 - Grammar

### Names

Names in JS cannot be one of these reserved words:

- _abstract_
- _boolean_ _break_ _byte_
- _case_ _catch_ _char_ _class_ _const_ _continue_
- _debugger_ _default_ _delete_ _do_ _double_
- _else_ _enum_ _export_ _extends_
- _false_ _final_ _finally_ _float_ _for_  _function_
- _goto_
- _if_ _implements_ _import_ _in_ _instanceof_  _int_ _interface_
- _long_
- _native_ _new_ _null_
- _package_ _private_ _protected_ _public_
- _return_
- _short_ _static_ _super_ _switch_ _synchronized_
- _this_ _throw_ _throws_ _transient_ _true_  _try_ _typeof_
- _var_ _volatile_ _void_
- _while_ _with_


### Numbers

- JS has a single number type. It is represented as **64-bit floating point** (the same as Java's double).
- There is no separate integer type, meaning that 1 and 1.0 are the same value. All you need to know about a number is that it is a number.
- Negative numbers are formed by using the **-** prefix operator.
- **NaN** is the result of an operation that cannot produce a normal result. **NaN** is not equal to any value, including itself. You can detect if a value is **NaN** with the _isNan()_ function.
- **Infinity** represents all values greater than the **MAX_VALUE** property, which has a value of approximately 1.79E+308.

### Strings

- All characters in JS are 16 bits wide.
- The \ (backslash) is the escape character.
- Strings are **immutable**, meaning it can never be changed.

### Statements

- When used inside a function, the **var** statement defines the function's **private** variables.
- A block is a set of statements wrapped in {}. Blocks in JS do not create a new scope - variables are local to the function. Therefore variables should be defined at the top of the function, not in blocks.
- List of _falsy_ values:
  * false
  * null
  * undefined
  * Empty string ' '
  * The number 0
  * The number NaN
- When using a _for in_ loop, usually a good idea to use `hasOwnProperty(variable)` to **make sure the property belongs to the object you want** and is not instead an inherited property from the prototype chain:
```javascript
for (myvariable in object) {
		if (object.hasOwnProperty(myvariable)) {
		... //statements to be executed
		}
}
```

- An expression statement can assign values, invoke a method and delete a property from an object.

### Expressions

- The **||** operator can be used to set _default_ values to a variable. As it produces the vale of its first operand if the first operand is truthy. Otherwise, it produces the value of the second operand.
```javascript
var myVariable = result || 5; // if result exists, use it. otherwise use 5 as default value.
```
- _Invocation_ is `(expression1, expression2, etc)`.
- _refinement_ is either `.name` or `[expression]` as used in an array.

### Literals

- Convenient notation for specifying new objects (object literals) or arrays (arra literals).
- Properties of the object are expressions and must be known at compile time.

### Functions

- A function literal defines a function value.
- It can specify a list of parameters that will act as variables initialized by the invocation arguments.

## Chapter 3 - Objects

- JS simple types:
  * numbers (**object-like**, as they have methods, but are **immutable**)
  * strings (**object-like**, as they have methods, but are **immutable**)
  * booleans (**object-like**, as they have methods, but are **immutable**)
  * null
  * undefined
- All other values are objects:
  * arrays
  * functions
  * regular expressions
  * objects
- Objects are **mutable** keyed collections.
- An object is a container of properties, where a property has a name (any string) and a value (anything except undefined).
- In JS, one object can inherit properties of another object from their prototype. This can reduce **initialization time** and **memory consumption**.

### Reference

Objects are passed around by reference. They are **never copied**.

```javascript
var myObj = {
  name: "Gabriel",
  role: "dev"
};

var clone = myObj;
clone.age = 23;
var age = myObj.age;
  // age is 23, because myObj and clone
  // are references to the same object.
```

### Prototype

- "Every object is linked to a prototype object from which it can inherit properties."
- The prototype is used only in **retrieval**. If we try to retrieve a property value from an object, and if the object does not contain this property, then **JS will go up the prototype chain and search for this property until it is found**. If the property does not exist, then the result will be _undefined_.
- Prototype has a dynamic relationship. If a new property is added to a prototype, that property will be **immediately visible** to all objects in the prototype chain.

### Reflection

- Reflection is used to determine which properties an object has.
- To determine the type of a property, the `typeof` operator can be used. **Any property on the prototype chain can produce a value**.
- The `hasOwnProperty` method does not look at the prototype chain. It will return true if the property exists in the object.

### Enumeration

- `for in` loops over all property names in an object, including functions and prototype properties.
- To filter out the values you don't want, use `typeof` or `hasOwnProperty`.
- One way to avoid looping over properties from the prototype chain is using `for` instead.
```javascript
var i;
var properties = [
	'day', 'month', 'year'
	];
for (i = 0; i < properties.length; i++) {
	document.writeIn(properties[i] + ':' + today[properties[i]]);
}
```

### Delete

- The `delete` operator can be used to remove a property from an object.
- It will remove a property from the object if it has one.
- It will not touch any of the objects up the prototype chain.
- If a property exists in the object and on its prototype, deleting it from the object will cause the prototype property to be retrieved.


### Global Abatement

- Global variables weaken the resiliency of programs and **should be avoided**.
- One way to minimize the use of global variables is creating a single global variable for your app. This variable will become the container of all info your app needs.

 
