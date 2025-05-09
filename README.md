# -Assignment01_L2
### What is the use of the keyof keyword in TypeScript? Provide an example.
The `keyof` keyword in TypeScript is used to get a **union type** of all the property names (keys) of a given type or interface.

**Use Case:**

It’s useful when you want to **safely access object properties** by name, ensuring that the property names are valid and type-checked.

---

 **Example:**

typescript
interface Person {
  name: string;
  age: number;
}

type PersonKeys = keyof Person;  // "name" | "age"

function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const person: Person = { name: "Alice", age: 30 };

const name = getProperty(person, "name");  // Type is string
const age = getProperty(person, "age");    // Type is number


###  Explanation:

* `keyof Person` becomes the union `"name" | "age"`.
* `getProperty` is a **generic function** that ensures:

  * `key` must be a valid key of the object `T`.
  * The return type is the type of the value at that key: `T[K]`.

###  Benefits:

 **Type safety**: Prevents invalid property access.
 **Autocomplete**: You get suggestions for valid keys in editors.
 **Flexibility**: Works well with reusable, generic utilities.






 ### What is Type Inference in TypeScript?

**Type inference** is the ability of TypeScript to automatically **deduce the type of a variable or expression** based on the assigned value, **without needing an explicit type annotation**.



### ✅ Example:

```typescript
let message = "Hello, TypeScript";
// TypeScript infers: message is of type string

let count = 5;
// TypeScript infers: count is of type number
```

In both examples, TypeScript **infers** the types `string` and `number` based on the assigned values.

---

###  Why Is It Helpful?

1. **Reduces boilerplate**:
   You don't need to manually specify types everywhere.

2. **Improves readability**:
   Less clutter in your code while maintaining type safety.

3. **Keeps the benefits of static typing**:
   Even without annotations, TypeScript can still catch type errors at compile time.

4. **Better development experience**:
   Code editors can offer intelligent autocompletion and inline documentation based on inferred types.

---

 Example with Function Inference:

```typescript
function add(a: number, b: number) {
  return a + b;
}
// TypeScript infers: return type is number

