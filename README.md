# TypeScript Study Notes

## Types

### Basic Types

- Primitive:
  - Boolean
  - Number
  - String
  - Symbol
  - Subtypes
    - Null
    - Undefined
- Object:
  - Array:
    ```typescript
    let list: number[] = [1, 2, 3];
    let list2: any[] = [1, ‘hello’]
    ```
  - Tuple:
    ```typescript
    let x: [string, number] = [10, ‘hello’];
    ```
  - Enum:
    ```typescript
    enum Color {Red, Green, Blue}  // automatically assign numbers: 0, 1, 2
    let index: Color = Color.Green;  // 1
    let name: string = Color[1];        // Green
    enum Color2 {Red = 1, Green = 2, Blue = 4} // override numbers
    let index: Color2 = Color2.Green;  // 2
    ```
- Any
- Function return types:
  - Void
  - Never: never return anything; function that throws an error
- Union:
    ```typescript
    let mix: number | string = 27;
    ```

### Function

- Return type

  ```typescript
  function sayHello(): void { console.log(‘Hello’) };
  ```

- Argument type
  
    ```typescript
    function add( a: number, b: number ): number { return a + b };
    ```

- Function type

  ```typescript
  let myAdd: ( a : number, b: number ) => number;
  myAdd = add;
  ```

### Type Assertion

  ```typescript
  let someValue: any = 'this is a string';
  let strLength: number = (someValue as string).length;
  ```

### Type Alias

  ```typescript
  type Complex = {
    data: number[],
    output: (all: boolean) => number[]
  };

  let complex: Complex = {
    data: [1, 2, 3],
    output: function (all: boolean): number[] {
      return this.data;
    }
  }
  ```

---

## Class

### Basics

```typescript
class Person {
  name: string;
  private type: string;   // can't be accessed from outside
  protected age: number = 28;  // can't be accessed from outside but can be inherited

  constructor(name: string) {
    this.name = name;
  }

  setType(type: string) {
    this.type = type;
  }

  private printAge() {
    console.log(this.age); // can access private property
  }
}

const person = new Person('Han');
console.log(person.name);
console.log(person.type); // error
person.setType('admin');
person.printAge();        // error
```

### Inheritance

```typescript
class Han extends Person {
  constructor() {
    super('Han');           // call parent class
    console.log(this.age);
    console.log(this.type); // can't access parent's private property
  }
}
const han = new Han();
```