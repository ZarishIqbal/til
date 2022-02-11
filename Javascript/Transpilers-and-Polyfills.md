### [Transpilers](https://javascript.info/polyfills)

A **_transpiler_** is a special piece of software that translates source code to another source code. It can parse (“read and understand”) modern code and rewrite it using older syntax constructs, so that it’ll also work in outdated engines.

> Example:
> JavaScript before year 2020 didn’t have the “nullish coalescing operator” ??. So, if a visitor uses an outdated browser, it may fail to understand the code.
>
> ```js
> // before running the transpiler
> height = height ?? 100;
>
> // after running the transpiler
> height = height !== undefined && height !== null ? height : 100;
> ```

**Babel** is one of the most prominent transpilers out there.

Modern project build systems, such as **_webpack_**, provide means to run transpiler automatically on every code change, so it’s very easy to integrate into development process.

### Polyfills

A **_polyfill_** is a script that updates/adds new functions. It fills in the gap and adds missing implementations.

> Example:
> The polyfill for Math.trunc is a script that implements it, like this:

> ```js
> if (!Math.trunc) {
>   Math.truc = function (number) {
>     // Math.ceil and Math.floor exist even in ancient JavaScript engines
>     // they are covered later in the tutorial
>     return number < 0 ? Math.ceil(number) : Math.floor(number);
>   };
> }
> ```

Two interesting libraries of polyfills are:

- core js that supports a lot, allows to include only needed features.
- polyfill.io service that provides a script with polyfills, depending on the features and user’s browser.
