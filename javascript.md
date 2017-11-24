## Pitfalls

### Scope
[Scopes basic fiddle](https://jsfiddle.net/spygi/cyrv6wzL/)
* Global, function (with var) or block (with let)
* Inner functions take the scope of the outer ones. Variable resolution happens with the innermost function first.

### Hoisting
[Hoisting with scope + reference system](https://jsfiddle.net/spygi/ttg00b6w/)

### Context 
[Callbacks + context](https://jsfiddle.net/spygi/v6L5sLqo/)

### Reference system
Same as Java's: call by value for simple values, objects references are passed by value which means if you change the whole reference you don't affect the original object
but if you modify the reference you modify the original too: [see here](https://jsfiddle.net/spygi/cv8zr0gm/)
