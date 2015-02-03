# protoscript

This is a fork and superset of [CoffeeScript](https://github.com/jashkenas/coffeescript) 1.0.1 that I did for a Programming Languages class. The original motivation was to augment CoffeeScript's "classes" with better language support for prototypal inheritance, but it has some other, general improvements as well.

- The `new` operator is overloaded to behave as JS's `new` or as `Object.create`, depending on context.
    - Not implemented in terms of `Object.create`, as it was not widely supported at the time.
- A new `isa` operator was added, which behaves as a hybrid between `typeof` and `instanceof` that additionally supports detecting prototypal inheritance.
- A new `as` operator was added for function binding.
    - `Function.prototype.bind` was not widely supported at the time.
- Object literal shorthand expanded to support expressions of the form `{ foo.bar }`.
- A `let` keyword was added to support IEFEs with pre-bound variables.
    - An equivalent feature came in CoffeeScript 1.3.1 in the form of `do` blocks special-casing default arguments.
- Overloaded functions can be declared via pattern matching, which do a weak form of pattern matching via the `isa` function.

Example of using overloaded functions to implement a curried `add` that also works with strings (for some reason?):

    add = function
      (String num) -> add parseInt(num, 10)
      (Number a) -> (b) -> add a, b
      (Number a, Number b) -> a + b

I'm not saying any of these are things CoffeeScript should have, or are particularly good ideas. That's just what you'll find in this repository.
