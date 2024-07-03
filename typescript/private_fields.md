# What are the differences between the private keyword and private fields in TypeScript?
If you use private fields in TypeScript and are targeting `ES2021` or older versions of JavaScript for your output, TypeScript will generate code that emulates the runtime behavior of private fields using 

typescript code
```typescript
class PrivateTS {
  private field = 10;
}

class PrivateJS {
  #field = 10;
}

const testTS = new PrivateJS();
const testJS = new PrivateJS();
```

compiled jacascript ES2021 code:
```javascript
"use strict";
var _PrivateJS_field;
class PrivateTS {
    constructor() {
        this.field = 10;
    }
}
class PrivateJS {
    constructor() {
        _PrivateJS_field.set(this, 10);
    }
}
_PrivateJS_field = new WeakMap();
const testTS = new PrivateJS();
const testJS = new PrivateJS();
```

### Other differences of note
Private fields are not returned by Object.getOwnPropertyNames and similar methods

Private fields are not serialized by JSON.stringify

There are importance edge cases around inheritance

TypeScript for example forbids declaring a private property in a subclass with the same name as a private property in the superclass.

```ts
class Base {
    private value = 1;
}


class Sub extends Base {
    private value = 2; // Compile error:
}
```
This is not true with private fields:

```ts
class Base {
    #value = 1;
}

class Sub extends Base {
    #value = 2; // Not an error
}
```

A private keyword private property without an initializer will not generate a property declaration in the emitted JavaScript:
```ts
class PrivateKeywordClass {
    private value?: string;
    getValue() { return this.value; }
}
```
Compiles to:

```js
class PrivateKeywordClass {
    getValue() { return this.value; }
}
```

Whereas private fields always generate a property declaration:
```ts
class PrivateKeywordClass {
    #value?: string;
    getValue() { return this.#value; }
}
```
Compiles to (when targetting esnext):
```js
class PrivateKeywordClass {
    #value;
    getValue() { return this.#value; }
}
```
