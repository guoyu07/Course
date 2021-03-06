# Today 12.04

### Terminal Cmder

Configurado para que el terminal cmder, que nada más abrirlo se abra en la ruta del proyecto. 
Para realizarlo, nos vamos al registro y creamos una nueva key (*valor de cadena expandible*) en la siguiente ruta: ```[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Command Processor]```
Ponemos el nombre de "*Autorun*" y escribimos la ruta de la siguiente manera: ```CD/d C:\Users\tonim\OneDrive\Documentos\SkyLab Coders\Course```

### Sublime acceso desde el terminal Cmder

En la carpeta donde tenemos el cmder, buscamos en archivo *user-aliases.cmd* localizado en ```\cmder\config```.
Añadimos al final del documento una nueva linea:
*subl="C:\Program Files\Sublime Text 3\sublime_text.exe" $1 -new_console:s75V*

Donde subl es la palabra clave para poder llamarla desde el terminal y el último valor ```-new_console:s75V``` es el tamaño de la ventana y la ```V``` corresponde a si lo queremos vertical y lo podemos cambiar por "H" para disposición horizontal. 

Despues en los ajustes del cmder, Main\Apparance\ desactivamos la casilla "Multiple consoles in one ConEmu windows", para poder verlo en ventanas separadas. :)

### [Funciones y funciones anónimas](https://github.com/juanmaguitar/javascript-notes/tree/master/markdown-en/04-functions#functions-scope).

Funciones anónimas son ejecutadas al instante, inicializadas mediante la variables.

Las funciones son datos

```javascript
function sum(a,b){
    return a+b
}
```

es lo mismo a:

```javascript 
var sum = function(a,b){return a+b}
```

En ambos el resultado del *typeOf* será function.

*[Call Back](http://stackoverflow.com/questions/483073/getting-%C2%AD%E2%80%90a-%C2%AD%E2%80%90better-%C2%AD%E2%80%90understanding-%C2%AD%E2%80%90of-%C2%AD%E2%80%90callback-%C2%AD%E2%80%90functions-%C2%AD%E2%80%90in-%C2%AD%E2%80%90javascript)*, función que llama a otra función, siempre dentro del argumento.
*When we pass a function A as an argument of another function B and B executes A, we tell that A is a*

```javascript
 function invoke_and_add(a, b){ return a() + b(); }
 function one() { return 1; }
 function two() { return 2; }
 invoke_and_add(one, two);

 invoke_and_add(one, function(){return 7;})
```

El scope (alcance) de las variables y  funciones.

Las funciones pueden ver sus variables locales, variables globales y el resto de funciones. Recorrido de "hijos a padres" serán reconocidos.

Esto se llama *scope chain*.

```javascript
 var a = 1;
function f(){
  var b = 1;
  function n() {
    var c = 3;
  }
}
```

*La variable C se podrá ver la b y la a. La var b podrá ver a y la var a colo verá la suya*

---

[argument](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Funciones/arguments)
---

Hoy en clase ha sido un dia duro con las globales locales y globales. :)

#[Javascript’s lexical scope, hoisting and closures without mystery.](https://medium.com/@nickbalestra/javascripts-lexical-scope-hoisting-and-closures-without-mystery-c2324681d4be)

Closures and closures example:

*In his book Kyle gives a very straightforward definition for what a closure is:
Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope.
If you think about lexical scope, this is so straight forward, cause scope is defined on author time and set in stone during compilation, therefore it have nothing to do with runtime and the call-stack(different will be if javascript will have been based on dynamic scope, but perhaps I will write a post about ‘this’ in the near future…). This mean that a function bar defined inside a function foo will have access to the outer scope of foo, also if being returned within it and invoked outside of foo, or in other words, outside of its scope,yes, its lexical scope! If it sounds complex, this latest example will make it clearer.*

```javascript
function timesCallFn() {
  var times = 1;
  return function() {
    return times++;
  }
};

var m = timesCallFn();
```

### Arrays & Objects

```javascript
var hero= {
    breed: "turtle",
    ocupation:"ninja"
};
```

```javascript
hero.breed // 'turtle'
hero['breed'] // 'turtle' de esta manera puede acceder mediante una variable.
```
*Ejemplo*

```javascript
var myProp ='breed'
hero[myProp] // 'turtle'
```

for in para poder recorrer las propiedades de un objeto y no suele utilizarse.

Una propiedad dentro de un objeto que contiene una función, se llama método.

Algunas de las distintas maneras de crear objetos:

1. example:
```javascript
var hero = {
  breed: 'Turtle',
  occupation: 'Ninja'
};
```

1. example:
```javascript
var hero = {};
hero.breed = 'turtle';
hero.name = 'Leonardo';
```

1. example:
```javascript
function createHero(){
    return{
      breed: 'Turtle',
  occupation: 'Ninja'
}
}
var hero= createHero();
```

1. example:
```javascript
function Hero(name) {
  this.name = name;
  this.occupation = 'Ninja';
  this.whoAreYou = function() {
    return "I'm " + this.name + " and I'm a " + this.occupation;
  }
}
```

1. example:
```javascript
var h1 = new Hero('Michelangelo');
var h2 = new Hero('Donatello');
```
