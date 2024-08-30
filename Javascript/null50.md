# 50 shades of null

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

![logo](../pix/null50.webp)

## JS undefined vs null

`undefined` semantically means the variable is declared but its value has not been defined yet.
- when serialized to Json the undefined properties of an object ARE NOT listed.
- accessing an undefined object properties raises an undefined error

`null` semantically means the variable is declared and its value is well defined, it is empty.
- when serialized to Json the null properties of an object ARE listed.
- accessing an null object properties also raises an undefined error

## TS any vs unknown

`any` is the most relax types, it tells the transpiler to let anything be assigned, invoked. No validation is performed. It means  **I don't care**.

_On the opposite,_

`unknown` is the most tight type, it tells the transpiler to stop anything be assigned, invoked. It means **I don't know**. I have to figure out.
Indeed, `unknown` is the mother type of all types.

## TS never

For a value to never occur:

```
function throwError(errorMsg: string): never { 
    throw new Error(errorMsg); 
} 

function keepProcessing(): never { 
    while (true) { 
         console.log('I always does something and never ends.')
    }
}
```

- Use `never` in positions where there will not or should not be a value
- Use `unknown` where there will be a value, but it might have any type
- Avoid using `any` unless you really need an unsafe escape hatch
## void

For a function to return no value:

```
function sayHi(): void { 
    console.log('Hi!')
} 
```

## Type guards

`instanceof` and `typeof`
