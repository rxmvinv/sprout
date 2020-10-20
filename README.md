# vue-local-app

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


App is written in Vue and and every element and value from TASK can be placed to one Main component but it's divided by small components to keep it structural.



About implemented steps:



I. In provided task we have two custom sets:

1. First custom set is alternative to our P from base. 

But because both are just math expressions and P isn't strictly defined 
I decided to return method as a value of P. And this method is checking both
expressions from base expression and from custom set expression.

2. Second custom set contains two new rules (conditions):

Second rule is used simply as extension (additional condition in our case);

But first rule from set supposed to overwrite our first base rule (by T value) from base (in base we have M value for this rule). But I decided to make combination of two values and because both of them are methods in particular case we can check each other. So for this rule/condition simple arrow function returning one of two methods is used either M or T.

Third item from custom set is supposed to overwrite our M expression. And here I also decided to extend M value so it contains both expressions from base and from custom set.

There were intentions to add some infinite chain of calls for these methods (M, P, T) until
satisfying result in K (float number) will be achieved. But as we have strict requirements:
condition => value/method and inputs provided by user (booleans and numbers) this plan was avoided.

Consider OUTPUTS from TASK as

methodM = M
methodP = P
methodT = T
methodH = H
resultK = K which is changed by methodK