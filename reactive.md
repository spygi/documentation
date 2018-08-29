## Redux
- [Egghead tutorial](https://egghead.io/courses/getting-started-with-redux)
- [Dataflow](https://redux.js.org/basics/dataflow)

## Reactive
- Reference [learnRxJS](https://www.learnrxjs.io) with links to official docs or this if [marbles](http://rxmarbles.com) is your thing
- [Operators index](http://reactivex.io/documentation/operators.html): at least some examples in rxjs are using the 4 syntax
- Version 6 main differences: pipe instead of chaining

### Intro
- [The missing intro](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754): Again using version 4
- [Intro rxjs 4](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/gettingstarted/creating.md)
- [Marble diagram for Observable](http://reactivex.io/documentation/observable.html)

### More
- [Don't unsubscribe](https://medium.com/@benlesh/rxjs-dont-unsubscribe-6753ed4fda87)
- [10 functions with examples](https://www.sitepoint.com/rxjs-functions-with-examples/)


### Thoughts
- Big API surface: map, switchMap, flatMap etc..
  - Which gets worse by having aliases eg. flatMap === mergeMap
  - And many overloads of the methods
  - Having the same methods on both Observable and instances of it doesn't help either
- Documentation/tutorials lagging behind current versions
- Not sure yet how big the advantage is

## Random
https://angular.io/guide/styleguide#shared-feature-module
https://medium.com/@cyrilletuzi/understanding-angular-modules-ngmodule-and-their-scopes-81e4ed6f7407
https://github.com/ngrx/platform/blob/master/docs/store/selectors.md
https://medium.com/@m3po22/stop-using-ngrx-effects-for-that-a6ccfe186399
