# Principios para escribir JavaScript consistente e idiomático

## Este es un documento que va a ir siendo actualizado y nuevas ideas para mejorar el código van a ser bien recibidios. En realidad este es un fork con la versión traducida del repo original https://github.com/rwldrn/idiomatic.js/ (inglés)  
## Todo el código en cualquier proyecto debería verse como si una sola persona lo hubiera escrito, no importa cuanta gente haya contribuido.

### La lista que se presenta a continuación destaca las prácticas que uso en todo el código del que soy autor, y las contribuciones a todos los proyectos que he creado, deben seguir estas prácticas.

### No intento imponer mis preferencias de estilo en el código de otras personas; si tienen un algún estilo común, esto debería ser respetado. 

## Translations

* [French](https://github.com/jfroffice/idiomatic.js/)
* [ORIGINAL] [English] (https://github.com/rwldrn/idiomatic.js/)

## Cosas importantes, no-idiomáticas:

### Calidad de código: Herramientas, recursos y referencias

 * [jsPerf](http://jsperf.com/)
 * [jsFiddle](http://jsfiddle.net/)
 * [jsbin](http://jsbin.com/)
 * [JavaScript Lint (JSL)](http://javascriptlint.com/)
 * [jshint](http://jshint.com/)
 * [jslint](http://jslint.org/)

[Usando herramientas de calidad de código - por Anton Kovalyov](http://anton.kovalyov.net/slides/gothamjs/)


### Volverse pro

[http://es5.github.com/](http://es5.github.com/)

Lo siguiente debería de ser considerado 1) es una incompleta, y 2) *REQUERIDA* lectura. No siempre estoy de acuerdo con el estilo escrito por los autores que acá abajo presento, pero una cosa es cierta: Son consistentes; y son autoridades en el lenguaje.

 * [Eloquent JavaScript](http://eloquentjavascript.net/)
 * [JavaScript, JavaScript](http://javascriptweblog.wordpress.com/)
 * [Rebecca Murphey](http://www.rebeccamurphey.com/) or [Adventures in JavaScript Development](http://rmurphey.com/)
 * [Perfection Kills](http://perfectionkills.com/)
 * [Douglas Crockford's Wrrrld Wide Web](http://www.crockford.com)
(Todos estos artículos están en inglés)

### Proceso de Build y Deployment

Los proyectos deberían siempre tratar de incluir algún mecanismo para que el código pueda ser comprimido para uso en producción. Algunos ejemplo de herramientas que hacen esto son [Uglify.js](https://github.com/mishoo/UglifyJS) (hecha en JavaScript), [Google Closure Compiler](http://code.google.com/closure/compiler/) (basado en java), y [YUI Compressor](http://developer.yahoo.com/yui/compressor/). Escoge uno y dale soporte.

Se puede entrar un "kit para build" genérico, ya funcional, en el directorio '/kits' de este mismo repositorio. El uso es sencillo: 1) copiar los contenidos de algún kit de la carpeta '/kits' a un nuevo directorio en el que se va a trabajar, 2) guarda el .js de tu proyecto en el directorio '/src' 3) incluir el nombre del proyecto en el archivo 'project.txt', 4) correr el comando 'make' desde la terminal.


### Testing

Los proyectos _deben_ incluir alguna forma de testing - unit testing, functional testing etc. Las demos NO SE CALIFICAN como "tests". A continuación se incluye una lista de frameworks para testing, ninguno de los cuales recomiendo más que otro.

 * [QUnit](http://github.com/jquery/qunit)
 * [Jasmine](https://github.com/pivotal/jasmine)
 * [Vows](https://github.com/cloudhead/vows)
 * [Mocha](https://github.com/visionmedia/mocha)
 * [Hiro](http://hirojs.com/)
 * [JsTestDriver](https://code.google.com/p/js-test-driver/)

## Tabla de contenidos

 * [Espacios en blanco](#whitespace)
 * [Beautiful Syntax](#spacing)
 * [Checkeo de tipos (Cortesía de la guía de estilo de jQuery)](#type)
 * [Evaluación condicional](#cond)
 * [Estilo práctico](#practical)
 * [Naming](#naming)
 * [Varios](#misc)
 * [Native & Host Objects](#native)
 * [Comentarios](#comments)


## Manifiesto de estilo idiomático


1. <a name="whitespace">Whitespace</a>

	* Nunca mezclar espacios y tabulaciones.
	* Cuando comienzas con un proyecto, antes de escribir código, escoger entre indentación blanda (espacios), o tabulaciones &mdash; Esto es LEY.
		* Para legibilidad, siempre recomiendo setear las preferencias de tu editor para que el tamaño de la identación sea de dos caracteres &mdash; esto significa, usar dos espacios, o que dos espacios representen una tabulación.
	* Si tu editor lo soporta, siempre trabajar con la preferencia para que se muestren los caracteres invisibles activada. Los beneficios de esta práctica son:
		* Refuerza la consistencia
		* Eliminar el espacio en blanco del fin de línea
		* Eliminar los espacios en blanco de las líneas vacías
		* Los commits y los diffs (comparar cambios contra versiones anteriores, etc.) va a ser mucho más fácil


2. <a name="spacing">Beautiful Syntax</a>

	A. Paréntesis, Llaves, Fines de línea

	```javascript

	// if/else/for/while/try siempre tienen espacios y se extienden a múltiples líneas
	// Esto mejora la legibilidad

	// 2.A.1.1
	// Ejemplos de sintaxis toda comprimida

	if(condition) doSomething();

	while(condition) iterating++;

	for(var i=0;i<100;i++) someIterativeFn();


	// 2.A.1.1
	// Uso de espacios para mejorar la legibilidad

	if ( condition ) {
		// statements
	}

	while ( condition ) {
		// statements
	}

	for ( var i = 0; i < 100; i++ ) {
		// statements
	}

	// Aún mejor:

	var i,
		length = 100;

	for ( i = 0; i < length; i++ ) {
		// statements
	}

	// O...

	var i = 0,
		length = 100;

	for ( ; i < length; i++ ) {
		// statements
	}

	var prop;

	for ( prop in object ) {
		// statements
	}


	if ( true ) {
		// statements
	} else {
		// statements
	}
	```


	B. Asignaciones, Declaraciones, Funciones (Nombradas, Expresiones, Constructores)

	```javascript

	// 2.B.1.1
	// Variables
	var foo = "bar",
		num = 1,
		undef;

	// Literal notations:
	var array = [],
		object = {};


	// 2.B.1.2
	// Usando solo una instancia de 'var' por scope (o sea, función), mejora la legibilidad
	// y mantiene tu lista de declaraciones claras (también ahorra de tipear un poco más)

	// Mal
	var foo = "";
	var bar = "";
	var qux;

	// Bien
	var foo = "",
		bar = "",
		quux;

	// o..
	var // comentar en éstos
	foo = "",
	bar = "",
	quux;

	```

	```javascript

	// 2.B.2.1
	// Declaración De Función Nombrada
	function foo( arg1, argN ) {

	}

	// Uso
	foo( arg1, argN );


	// 2.B.2.2
	// Declaración De Función Nombrada
	function square( number ) {
		return number * number;
	}

	// Uso
	square( 10 );

	// Really contrived continuation passing style
	function square( number, callback ) {
		callback( number * number );
	}

	square( 10, function( square ) {
		// callback statements
	});


	// 2.B.2.3
	// Expresión de función
	var square = function( number ) {
		// Retornar algo relevante y con valor agregado 
		return number * number;
	};

	// Expresión de función con identificador
	// Esta forma es preferida porque tiene el valor agregado de 
	// poder ser llamada a sí misma y ser identificable en el stacktrace (MUY útil para debugging) :
	var factorial = function factorial( number ) {
		if ( number < 2 ) {
			return 1;
		}

		return number * factorial( number-1 );
	};


	// 2.B.2.4
	// Declaración de Constructor
	function FooBar( options ) {

		this.options = options;
	}

	// Uso
	var fooBar = new FooBar({ a: "alpha" });

	fooBar.options;
	// { a: "alpha" }

	```


	C. Algunas excepciones

	```javascript

	// 2.C.1.1
	// Funciones con callbacls
	foo(function() {
		// Como se ve no hay espacio entre el primer paréntesis 
		// y la palabra "function"
	});

	// Función que acepta un Array como parámetro, sin espacio entre ([ 
	foo([ "alpha", "beta" ]);

	// 2.C.1.2
	// Función que acepta un objeto, sin espacio
	foo({
		a: "alpha",
		b: "beta"
	});

	// Grupo de paréntesis dentro de paréntesis, sin espacio
	if ( !("foo" in obj) ) {

	}

	```

	D. La consistencia siempre gana

	En las secciones 2.A-2.C, las reglas para los espacios son puestas con un objetivo mas simple y con un propósito más general: consistencia.
	Es importante destacar que algunas preferencias de formato, deberían ser consideradas opcionales, pero solo un estilo debería existir a través de todo el código de fuente de tu proyecto.

	```javascript

	// 2.D.1.1

	if (condition) {
		// statements
	}

	while (condition) {
		// statements
	}

	for (var i = 0; i < 100; i++) {
		// statements
	}

	if (true) {
		// statements
	} else {
		// statements
	}

	```

	E. Fin de línea y líneas vacías

	Espacios en blanco pueden arruinar diffs y hacer los cambios imposibles leer. Considera agregar algún mecanismo para remover automáticamente los espacios que se encuentran al final de la línea o en líneas vacías.

3. <a name="type">Checkeo de tipos (Cortesía de la guía de estilo de jQuery)</a>

	3.A Tipos

	* String:

		`typeof variable === "string"`

	* Number:

		`typeof variable === "number"`

	* Boolean:

		`typeof variable === "boolean"`

	* Object:

		`typeof variable === "object"`

	* Array:

		`Array.isArray(arrayObject)`
		(cuando sea posible / hay implementaciónes que no tienen esta función)

	* null:

		`variable === null`

	* null or undefined:

		`variable == null`

	* undefined:

		* Variables globales:

			* `typeof variable === "undefined"`

		* Variables locales:

			* `variable === undefined`

		* Propiedades:
			* `object.prop === undefined`
			* `object.hasOwnProperty( prop )`
			* `"prop" in object`


	JavaScript es un lenguaje dinámicamente tipado - lo que puede ser tu mejor amigo o tu peor enemigo, entonces: Siempre respeta al 'type' como se recomienda.

	3.B Coerción de tipos

	Considera lo que causaría lo siguiente...

	Dado este HTML:

	```html

	<input type="text" id="foo-input" value="1">

	```


	```js

	// 3.B.1.1

	// 'foo' ha sido declarado con el valor '0' y su tipo es 'number'
	var foo = 0;

	// typeof foo;
	// "number"
	...

	// En algún lugar, más tarde en tu código, necesitas modificar 'foo'
	// con un nuevo valor derivado de el elemento input del HTML

	foo = document.getElementById("foo-input").value;

	// Si vas a testear 'typeof foo' ahora, el resultado sería 'string'
	// Esto significa que si hubieras tenido lógica que comparara 'foo' así:

	if ( foo === 1 ) {

		importantTask();

	}

	// `importantTask()` nunca habría sido evaluada, incluso con 'foo' teniendo un valor de "1" 

	// 3.B.1.2

	// Te le podés adelantar a los problemas, usando coerción de tipos con los operadores unarios + o - :

	foo = +document.getElementById("foo-input").value;
	      ^ el operador unario + va a convertir su operando derecho a number

	// typeof foo;
	// "number"

	if ( foo === 1 ) {

		importantTask();

	}

	// `importantTask()` va a ser llamada
	```

	Aquí hay algunos casos comunes con coerciones:


	```javascript

	// 3.B.2.1

	var number = 1,
		string = "1",
		bool = false;

	number;
	// 1

	number + "";
	// "1"

	string;
	 // "1"

	+string;
	// 1

	+string++;
	// 1

	string;
	// 2

	bool;
	// false

	+bool;
	// 0

	bool + "";
	// "false"
	```


	```javascript
	// 3.B.2.2

	var number = 1,
		string = "1",
		bool = true;

	string === number;
	// false

	string === number + "";
	// true

	+string === number;
	// true

	bool === number;
	// false

	+bool === number;
	// true

	bool === string;
	// false

	bool === !!string;
	// true
	```

	```javascript
	// 3.B.2.3

	var array = [ "a", "b", "c" ];

	!!~array.indexOf( "a" );
	// true

	!!~array.indexOf( "b" );
	// true

	!!~array.indexOf( "c" );
	// true

	!!~array.indexOf( "d" );
	// false


	var num = 2.5;

	parseInt( num, 10 );

	// is the same as...

	~~num;

	```

4. <a name="cond">Conditional Evaluation</a>

	```javascript

	// 4.1.1
	// When only evaluating that an array has length,
	// instead of this:
	if ( array.length > 0 ) ...

	// ...evaluate truthiness, like this:
	if ( array.length ) ...


	// 4.1.2
	// When only evaluating that an array is empty,
	// instead of this:
	if ( array.length === 0 ) ...

	// ...evaluate truthiness, like this:
	if ( !array.length ) ...


	// 4.1.3
	// When only evaluating that a string is not empty,
	// instead of this:
	if ( string !== "" ) ...

	// ...evaluate truthiness, like this:
	if ( string ) ...


	// 4.1.4
	// When only evaluating that a string _is_ empty,
	// instead of this:
	if ( string === "" ) ...

	// ...evaluate falsy-ness, like this:
	if ( !string ) ...


	// 4.1.5
	// When only evaluating that a reference is true,
	// instead of this:
	if ( foo === true ) ...

	// ...evaluate like you mean it, take advantage of it's primitive capabilities:
	if ( foo ) ...


	// 4.1.6
	// When evaluating that a reference is false,
	// instead of this:
	if ( foo === false ) ...

	// ...use negation to coerce a true evaluation
	if ( !foo ) ...

	// ...Be careful, this will also match: 0, "", null, undefined, NaN
	// If you _MUST_ test for a boolean false, then use
	if ( foo === false ) ...


	// 4.1.7
	// When only evaluating a ref that might be null or undefined, but NOT false, "" or 0,
	// instead of this:
	if ( foo === null || foo === undefined ) ...

	// ...take advantage of == type coercion, like this:
	if ( foo == null ) ...

	// Remember, using == will match a `null` to BOTH `null` and `undefined`
	// but not `false`, "" or 0
	null == undefined

	```
	ALWAYS evaluate for the best, most accurate result - the above is a guideline, not a dogma.

	```javascript

	// 4.2.1
	// Type coercion and evaluation notes

	Prefer `===` over `==` (unless the case requires loose type evaluation)

	=== does not coerce type, which means that:

	"1" === 1;
	// false

	== does coerce type, which means that:

	"1" == 1;
	// true


	// 4.2.2
	// Booleans, Truthies & Falsies

	Booleans: true, false

	Truthy are: "foo", 1

	Falsy are: "", 0, null, undefined, NaN, void 0

	```


5. <a name="practical">Practical Style</a>

	```javascript

	// 5.1.1
	// A Practical Module

	(function( global ) {
		var Module = (function() {

			var data = "secret";

			return {
				// This is some boolean property
				bool: true,
				// Some string value
				string: "a string",
				// An array property
				array: [ 1, 2, 3, 4 ],
				// An object property
				object: {
					lang: "en-Us"
				},
				getData: function() {
					// get the current value of `data`
					return data;
				},
				setData: function( value ) {
					// set the value of `data` and return it
					return ( data = value );
				}
			};
		})();

		// Other things might happen here

		// expose our module to the global object
		global.Module = Module;

	})( this );

	```

	```javascript

	// 5.2.1
	// A Practical Constructor

	(function( global ) {

		function Ctor( foo ) {

			this.foo = foo;

			return this;
		}

		Ctor.prototype.getFoo = function() {
			return this.foo;
		};

		Ctor.prototype.setFoo = function( val ) {
			return ( this.foo = val );
		};


		// To call constructor's without `new`, you might do this:
		var ctor = function( foo ) {
			return new Ctor( foo );
		};


		// expose our constructor to the global object
		global.ctor = ctor;

	})( this );

	```



6. <a name="naming">Naming</a>


	You are not a human code compiler/compressor, so don't try to be one.

	The following code is an example of egregious naming:

	```javascript

	// 6.1.1
	// Example of code with poor names

	function q(s) {
		return document.querySelectorAll(s);
	}
	var i,a=[],els=q("#foo");
	for(i=0;i<els.length;i++){a.push(els[i]);}
	```

	Without a doubt, you've written code like this - hopefully that ends today.

	Here's the same piece of logic, but with kinder, more thoughtful naming (and a readable structure):

	```javascript

	// 6.2.1
	// Example of code with improved names

	function query( selector ) {
		return document.querySelectorAll( selector );
	}

	var idx = 0,
		elements = [],
		matches = query("#foo"),
		length = matches.length;

	for( ; idx < length; idx++ ){
		elements.push( matches[ idx ] );
	}

	```

	A few additional naming pointers:

	```javascript

	// 6.3.1
	// Naming strings

	`dog` is a string


	// 6.3.2
	// Naming arrays

	`dogs` is an array of `dog` strings


	// 6.3.3
	// Naming functions, objects, instances, etc

	camelCase; function and var declarations


	// 6.3.4
	// Naming constructors, prototypes, etc.

	PascalCase; constructor function


	// 6.3.5
	// Naming regular expressions

	rDesc = //;


	// 6.3.6
	// From the Google Closure Library Style Guide

	functionNamesLikeThis;
	variableNamesLikeThis;
	ConstructorNamesLikeThis;
	EnumNamesLikeThis;
	methodNamesLikeThis;
	SYMBOLIC_CONSTANTS_LIKE_THIS;



	```

7. <a name="misc">Misc</a>

	This section will serve to illustrate ideas and concepts that should not be considered dogma, but instead exists to encourage questioning practices in an attempt to find better ways to do common JavaScript programming tasks.

	A. Using `switch` should be avoided, modern method tracing will blacklist functions with switch statements

	There seems to be drastic improvements to the execution of `switch` statements in latest releases of Firefox and Chrome.
	http://jsperf.com/switch-vs-object-literal-vs-module

	Notable improvements can be witnesses here as well:
	https://github.com/rwldrn/idiomatic.js/issues/13

	```javascript

	// 7.A.1.1
	// An example switch statement

	switch( foo ) {
		case "alpha":
			alpha();
			break;
		case "beta":
			beta();
			break;
		default:
			// something to default to
			break;
	}

	// 7.A.1.2
	// A better approach would be to use an object literal or even a module:

	var switchObj = {
		alpha: function() {
			// statements
			// a return
		},
		beta: function() {
			// statements
			// a return
		},
		_default: function() {
			// statements
			// a return
		}
	};

	var switchModule = (function () {
		return {
			alpha: function() {
				// statements
				// a return
			},
			beta: function() {
				// statements
				// a return
			},
			_default: function() {
				// statements
				// a return
			}
		};
	})();


	// 7.A.1.3
	// If `foo` is a property of `switchObj` or `switchModule`, execute as a method...

	( switchObj.hasOwnProperty( foo ) && switchObj[ foo ] || switchObj._default )( args );

	( switchModule.hasOwnProperty( foo ) && switchModule[ foo ] || switchModule._default )( args );

	// If you know and trust the value of `foo`, you could even omit the OR check
	// leaving only the execution:

	switchObj[ foo ]( args );

	switchModule[ foo ]( args );


	// This pattern also promotes code reusability.

	```

	B. Early returns promote code readability with negligible performance difference

	```javascript

	// 7.B.1.1
	// Bad:
	function returnLate( foo ) {
		var ret;

		if ( foo ) {
			ret = "foo";
		} else {
			ret = "quux";
		}
		return ret;
	}

	// Good:

	function returnEarly( foo ) {

		if ( foo ) {
			return "foo";
		}
		return "quux";
	}

	```


8. <a name="native">Native & Host Objects</a>

	The basic principal here is:

	### Don't do stupid shit and everything will be ok.

	To reinforce this concept, please watch the following presentation:

	#### “Everything is Permitted: Extending Built-ins” by Andrew Dupont (JSConf2011, Portland, Oregon)

	<iframe src="http://blip.tv/play/g_Mngr6LegI.html" width="480" height="346" frameborder="0" allowfullscreen></iframe><embed type="application/x-shockwave-flash" src="http://a.blip.tv/api.swf#g_Mngr6LegI" style="display:none"></embed>

	http://blip.tv/jsconf/jsconf2011-andrew-dupont-everything-is-permitted-extending-built-ins-5211542


9. <a name="comments">Comments</a>

	* JSDoc style is good (Closure Compiler type hints++)
	* Single line above the code that is subject
	* Multiline is good
	* End of line comments are prohibited!



## Appendix

### Comma First.

Any project that cites this document as its base style guide will not accept comma first code formatting unless explicitly specified otherwise.

See: https://mail.mozilla.org/pipermail/es-discuss/2011-September/016805.html
Notable: "That is horrible, and a reason to reject comma first.", "comma-first still is to be avoided"
