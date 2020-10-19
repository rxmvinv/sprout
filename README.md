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


How to run this Vue small test app is described above.

About implemented steps:

Several tryings for calculation of result were implemented.
Expecting result is a float number so if calculation doesn't work
user requested to change conditions. There are several methods for one 
condition (A && B && !C). In theory with customs handling 
only one should be chosen either T or M but in implementation you can find
checking of first one and if result isn't satisfying returning of second. So
at some condition T is turning to anonymous function which is returning on of two methods

There were intentions to add some infinite ring of calls of these methods (M, P, T) until
satisfying result in K (float number) will be achieved. But as we have strict requirements:
condition => value (method in our particullar case) and inputs provided by user (booleans and numbers) this plan was avoided.

About implementation by Vue:
As we have simple elements actually everything can be placed to one Main component but to implement some structure typical for such a frameworks structure was devided by smaller components: NumberValue, FinalResult etc.