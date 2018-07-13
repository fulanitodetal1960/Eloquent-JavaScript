{{meta {docid: values}}}

# Valores, Tipos y Operadores

{{quote {author: "Master Yuan-Ma", title: "The Book of Programming", chapter: true}

Bajo la superficie de la máquina, el programa se mueve. Sin esfuerzo,se expande y contrae. En gran armonía, los electrones se dispersan y reagrupan. Las formas en el monitor no son más que ondas en el agua. La esencia permanece invisible más abajo.

quote}}

{{figure {url: "img/chapter_picture_1.jpg", alt: "Picture of a sea of bits", chapter: framed}}}

Dentro del mundo de la computadora, solo hay datos. Puede leer datos, modificar datos, crear nuevos datos, pero no se pueden hablar de lo que no es un datos. Todos estos datos se almacenan como largas secuencias de bits y, por lo tanto, son fundamentalmente iguales.

Los _bits_ son una clase deobjeto con dos valores, generalmente descritos como ceros y unos. Dentro de la computadora, toman formas tales como una carga eléctrica alta o baja, una señal fuerte o débil, o una mancha brillante o sin brillo en la superficie de un CD. Cualquier parte de información discreta puede reducirse a una secuencia de ceros y unos y, por lo tanto, representarse en bits.

Por ejemplo, podemos expresar el número 13 en bits. Funciona igual que un número decimal, pero en lugar de 10 dígitos diferentes,tiene solo 2, y el peso de cada uno aumenta en un factor de 2 de  derecha a izquierda. Aquí están los bits que componen el número 13, con el peso de los dígitos que se muestra debajo de ellos:

```
   0   0   0   0   1   1   0   1
 128  64  32  16   8   4   2   1
```

Así que este es el número binario 00001101. Sus dígitos distintos de cero representan8, 4 y 1, que suman 13.

## Valores

Imagine un mar de bits: un océano de ellos. Una computadora moderna típica tiene más de 30 mil millones de bits en su almacenamiento de datos volátil (memoria de trabajo). El almacenamiento no volátil (el disco duro o equivalente) tiende a tener todavía algunos órdenes de magnitud más.

Para poder trabajar con tales cantidades de bits sin perderse, debemos separarlos en pedazos que representen trozos de información. En el entorno JavaScript, esos fragmentos se llaman _valores_. Aunque todos los valores están hechos de bits, juegan diferentes roles. Cada valor tiene un tipo que determina su función. Algunos valores son números, algunos son fragmentos de texto, algunos son funciones, etc.

Para crear un valor, solo debe invocar su nombre. Esto es bueno. No tiene que recolectar material para sus valores o pagar por ellos. Solo los llama, y _woo_, lo tienes. En realidad, no se crean de la nada, por supuesto. Cada valor debe almacenarse en algún lugar, y si desea usar una cantidad enorme de ellos al mismo tiempo, es posible que se quede sin memoria. Afortunadamente, esto es un problema solo si los necesitas todos simultáneamente. Tan pronto como ya no use un valor, se disipará, dejando atrás sus bits para ser reciclados como material para la próxima generación de valores.

En este capítulo se presentan los elementos atómicos de los programas JavaScript, es decir, los valores de tipo simple y los operadores que pueden actuar sobre los mismos.

## Números

Los valores del tipo _number_ son, como era de esperar, valores numéricos. Een un Programa JavaScript, están escritos de la siguiente manera:

```
13
```

Úselo en un programa y forzará que se active el patrón de bits para el número 13  dentro de la memoria de la computadora.

JavaScript usa una cantidad fija de bits, 64, para almacenar un único valor numérico. Solo hay tantos patrones como los que se puedan representar con 64 bits, lo que significa que la cantidad de números diferentes que se pueden representar es limitada. Con _N_ digitos decimales, puede representar 10 ^ N ^ números. De manera similar, dados 64 dígitos binarios, puede representar 2 ^ 64 ^ números diferentes, que es aproximadamente 18 quintillones (18 con 18 ceros detras). Eso es mucho.

La memoria de la computadora antes solían ser mucho más pequeñas, y las personas tendían a usar grupos de 8 o 16 bits para representar sus números. Era facil _desbordar_ accidentalmente esos pequeños números, y terminar con un número que no encajaba en la cantidad dada de bits. Hoy, incluso las computadoras que caben en su bolsillo tienen mucha memoria, por lo que puede usar fragmentos de 64 bits, y solo debe preocuparse por el desbordamiento cuando se trata de números verdaderamente astronómicos.

Sin embargo, no todos los números enteros menores de 18 quintillones caben en un número de JavaScript. Esos bits también almacenan números negativos, por lo que un bit indica el signo del número. Otro problema aun mayor es que los números no enteros también deben estar representados. Para conseguirlo, algunos de los bits se usan para almacenar la posición del punto decimal. El número entero real máximo que puede almacenarse está myor que el rango de 9 cuatrillones (15 ceros), que sigue siendo bastamente grande.

Los números fraccionarios se escriben usando un punto.

```
9.81
```

Para los números muy grandes o muy pequeños, también puede usarse la notacion científica agregando una _e_ (para el _exponente_), seguida del exponente del número.

```
2.998e8
```

Es decir 2.998 × 10^8^ = 299,800,000.

Los cálculos con números _enteros_, más pequeños que los 9 cuatrillones antes mencionados, tienen la garantia de ser siempre precisos. Desafortunadamente, los cálculos con números fraccionarios generalmente no lo son. Así como π (pi) no se puede expresar con precisión mediante un número finito de dígitos decimales, muchos números pierden algo de precisión cuando solo se dispone de 64 bits para almacenarlos. Es una pena, pero solo causa problemas prácticos en situaciones específicas. Lo importante es tenerlo en cuenta y tratar los números fraccionarios digitales como aproximaciones, no como valores precisos.

### Aritmética

El propósito principal de los números es realizar operaciones aritmética. Las operaciones aritmeticas como la adición o la multiplicación cogen dos valores numéricos y producen nuevo valor númerico con ellos. Así es como se ven en JavaScript:

```
100 + 4 * 11
```

Los símbolos `+` y `*` se llaman _operadores_. El primero significa adición, y el segundo significa multiplicación. Al poner un operador entre dos valores, se le aplicará a esos valores y se generará un nuevo valor.

Pero, ¿se quiere en el ejemplo anterior  "sumar 4 y 100, y multiplicar el resultado por 11" o se multiplica antes de sumar? Como habrás adivinado, se multiplica primero. Pero como en matemáticas, puedes cambiar este orden al envolver la suma entre paréntesis.

```
(100 + 4) * 11
```

Para la resta, está el operador `-`, y la división se puede hacer
con el operador `/`.

Cuando los operadores aparecen juntos sin paréntesis, el orden en que se aplican está determinado por la _ precedencia _ de los operadores. El ejemplo muestra que la multiplicación va antes de la suma. El operador `/` tiene la misma precedencia que `*`. Del mismo modo que el `+` y el `-`. Cuando varios operadores con la misma precedencia aparecen uno al lado del otro, como en `1 - 2 + 1`, se aplican de izquierda a derecha:` (1 - 2) + 1`.

Estas reglas de precedencia no son algo de lo que deba preocuparse. En caso de duda, simplemente agregue paréntesis.

Hay un operador aritmético más, que puede que no reconozca de inmediato. El símbolo `%` se usa para representar la operación _resto_. `X% Y` es el resto de la división de` X` entre `Y`. Por ejemplo, `314% 100` produce` 14`, y `144% 12` da` 0`. La precedencia del operador resto es la misma que la de multiplicación y división. También verá a menudo este operador con la denominación _modulo_.

### Números especiales

Hay tres valores especiales en JavaScript que se considerannúmeros, pero no se comportan como los números normales.

Los dos primeros son `Infinito` y` -Infinito`, que representan los infinitos positivos y negativos. `Infinito - 1` sigue siendo` Infinito`, y así sucesivamente. Sin embargo, no confíe demasiado en el cálculo basado en el infinito. No es matemáticamente sólida, y conducirá rápidamente al siguiente número especial: `NaN`.

`NaN` significa" no es un número ", aunque es un valor de tipo de número. Obtendrá este resultado cuando, por ejemplo, intente calcular `0 / 0` (cero dividido entre cero),` Infinito - Infinito`, o cualquier cantidad de otras operaciones numéricas que no den un resultado significativo.

## Strings (cadena de caracteres)

El siguiente tipo de datos básicos es _string_. Las cadenas de caracterees se usan para representar texto. se escriben encerrando su contenido entre comillas.

```
`Down on the sea`
"Lie on the ocean"
'Float on the ocean'
```

Puede usar comillas `backticks`, comillas dobles o comillas simples rectas, siempre que las comillas al principio y al final de la cadena coincidan.

Puede poner entre comillas casi cualquier cosa, y JavaScript creara un valor de tipo _string_. Aun asi algunos caracteres son difíciles de entrecomillar. Puedes imaginar cómo poner unas comillas entre comillas, puede ser difícil. _Newlines_ (el caracter [enter]{nombre de la tecla}) se puede poner incluir sin escaparlas solo cuando la cadena se entrecomilla con comillas backticks (`` ` ``).

Para que sea posible incluir dichos caracteres en una cadena, se utiliza la siguiente notación: siempre que se encuentre una barra invertida (`\`) dentro del texto entre comillas, indica que el carácter que le sigue tiene un significado especial. A este caracter se le llama _escaping_. Una comilla precedida de una barra invertida no terminará la cadena sino que será parte de ella. Cuando aparece un carácter `n` después de una barra invertida, se interpreta como una nueva línea. Del mismo modo, un `t` después de una barra invertida significa un carácter de tabulación. Tome la siguiente cadena:

```
"This is the first line\nAnd this is the second"
```

El contenido real del texto es este:

```
{lang: null}
This is the first line
And this is the second
```

Hay, por supuesto, situaciones en las que desea que una barra invertida en una cadena sea solo una barra invertida, no un código especial. Si dos barras diagonales inversas se suceden, se colapsarán y solo quedará una en el valor de cadena resultante. Así es como se puede expresar la cadena "_El carácter nueva línea se escribe como `"` \ n`"` ._ ":

```
"A newline character is written like \"\\n\"."
```
ó
```
'A newline character is written like "\\n".'
```
Las cadenas de caracteres, también, tienen que modelarse como una serie de bits para poder existir dentro de la computadora. La forma en que JavaScript hace esto se basa en el estándar _Unicode_. Esta norma asigna un número a prácticamente todos los caracteres que necesites, incluidos los caracteres de griego, árabe, japonés, armenio, etc. Si tenemos un número para cada caracter, un string se puede describir con una secuencia de números.

Y eso es lo que hace JavaScript. Pero hay una complicación: la representación de JavaScript utiliza 16 bits por cada elemento de una cadena de caracteres, que puede describir hasta 2 ^ 16 ^ caracteres diferentes. Pero Unicode define más que esos caracteres, casi el doble. Por lo tanto, algunos caracteres, como muchos emoji, ocupan dos "posiciones de caracter" en las cadenas de caracteres de JavaScript. Volveremos a esto en [Chapter5](higher_order#code_units).

Las cadenas no se pueden dividir, multiplicar o restar, pero pueden usar el operador `+` en ellas. Este no suma, sino _concatena_, une dos cadenas. La siguiente línea producirá la cadena `" concatenate"`:

```
"con" + "cat" + "e" + "nate"
```

Los valores de cadena tienen una serie de funciones asociadas (_metodos_) que se pueden usar para realizar operaciones en ellas. Veremos más sobre esto en [Capítulo 4](data#methods).

Las cadenas escritas con comillas simples o dobles se comportan de manera muy similar; la única diferencia es saber qué tipo de comillas necesitas escapar dentro de ellas. Las cadenas entrecomilladas con `comillas simples - backtick`, generalmente llamadas _template literals_, pueden hacer más cosas. Además de poder extender líneas, también pueden incrustar otros valores.

```
`half of 100 is ${100 / 2}`
```

Cuando escribe algo en el interior de `$ {}` en una cadena entrecomillada con `backtick`, su resultado será computado, y convertido en una cadena, e incluido en esa posición. El ejemplo produce "_half of 100 is 50_".

## Operadores Unarios

No todos los operadores son símbolos. Algunos están escritos como palabras. Un ejemplo es el operador `typeof`, que produce un valor de cadena que muestra el nombre del `tipo` que tiene el valor.

```
console.log(typeof 4.5)
// → number
console.log(typeof "x")
// → string
```

Usaremos `console.log` en el código de ejemplo para indicar que queremos ver el resultado de evaluar algo. Veremos más sobre esto en el [próximocapítulo](program_structure).

Los demas operadores mostrados operaron sobre dos valores, pero `typeof` solo sobre uno. Los operadores que usan dos valores se llaman operadores _binarios_, mientras que los que usan uno se llaman operadores _unarios_. El operador menos ``"-"`` se puede usar como operador binario y como operador unario.

```
console.log(- (10 - 2))
// → -8
```

## Valores Booleanos

A menudo es útil tener un valor que distinga nada más entre dos posibilidades, como "sí" y "no" o "encendido" y "apagado". Para este propósito, JavaScript tiene el `tipo` _Booleano_, que tiene solo dos valores, verdadero y falso , que se escriben `true` y `false`.

### Comparación

Esto es una manera de producir valores booleanos:

```
console.log(3 > 2)
// → true
console.log(3 < 2)
// → false
```

Los signos `>` y `<` son los símbolos tradicionales para representar "es mayor que" y "es menor que", respectivamente. Son operadores binarios. Al aplicarlos, se obtiene un valor booleano que indica si es verdadero o falso.

Las cadenas se pueden comparar de la misma manera.

```
console.log("Aardvark" < "Zoroaster")
// → true
```

La forma en que se ordenan las cadenas es más o menos alfabéticamente, pero no es exactamente lo que esperaría ver en un diccionario: las letras mayúsculas siempre son "menos" que las minúsculas, por lo que `" Z "<" a "`, también se incluyen en la ordenacion los caracteres no alfabéticos (!, -, y demás) . Al comparar cadenas, JavaScript revisa los caracteres de izquierda a derecha, comparando los códigos _Unicode_ uno por uno.

Otros operadores similares son `> =` (mayor o igual que), `<=` (menor o igual que), `==` (igual a) y `! =` (No igual a).

```
console.log("Itchy" != "Scratchy")
// → true
console.log("Apple" == "Orange")
// → false
```

Solo hay un valor en JavaScript que no es igual a sí mismo, y ese es `NaN` (" not a number ").

```
console.log(NaN == NaN)
// → false
```

`NaN` se supone que denota el resultado de un cálculo sin sentido,y, como tal, no es igual al resultado de cualquier otro cálculo sin sentido.

### Operadores logicos

También hay algunas operaciones que se pueden aplicar a valores booleanos. JavaScript admite tres operadores lógicos: _and_, _or_ y _not_. Estos pueden usarse para "razonar" con valores Booleanos.

El operador `&&` representa al _y_ lógico. Es un operador binario, y su resultado es verdadero solo si ambos valores son verdaderos.

```
console.log(true && false)
// → false
console.log(true && true)
// → true
```

El operador `||` representa al _or_ lógico. Produce verdadero si cualquiera de sus valores es verdadero.

```
console.log(false || true)
// → true
console.log(false || false)
// → false
```

_Not_ está representado por el signo de exclamación (`!`). Es un operador unario que invierte el valor que le dan - `! true` produce` false`, y `! false` da `verdadero`.

Al mezclar estos operadores booleanos con la aritmética y otros operadores, no siempre es obvio cuando se necesitan paréntesis. En la práctica, por lo general, puede salir adelante sabiendo que, de los operadores que hemos visto hasta ahora, `||` tiene la precedencia más baja, luego viene `&&`, luego los operadores de comparación (`>`, `==`, y etc.) y luego el resto. Este orden ha sido elegido de tal manera que, en expresiones típicas como la siguiente, se necesitan el menor número de paréntesis posible:

```
1 + 1 == 2 && 10 * 10 > 50
```

El último operador lógico que analizaré no es unario, ni es binario, sino _terciario_, opera con tres valores. Está escrito con un signo de interrogación y dos puntos, asi:

```
console.log(true ? 1 : 2);
// → 1
console.log(false ? 1 : 2);
// → 2
```

Se llama operador _condicional_ (algunas veces  operador _ternario_ ya que es el único operador de este tipo en el lenguaje). El valor a la izquierda del signo de interrogación "elige" cuál de los otros dos valores sera elegido. Cuando es verdadero, elige el izquierdo, y cuando es falso, elige el valor derecho.

## Valores vacíos

Hay dos valores especiales,  `null` y` undefined`, que se utilizan para denotar la ausencia de un valor _significativo_. Son en si mismos valores, pero no tienen ninguna información.

Muchas de las operaciones en el idioma que no producen un valor significativo (verá algunas más tarde) dan `undefined` simplemente porque tienen que tener _algun_ valor.

La diferencia de significado entre `undefined` y` null` es un accidente del diseño de JavaScript, y no importa la mayor parte del tiempo. En los casos en que realmente tenga que preocuparse por estos valores, recomiendo tratarlos como intercambiables en su mayoría.

## Conversión automática de tipo

En la Introducción, mencioné que JavaScript hace todo lo posible para aceptar casi cualquier programa que le des, incluso programas que hacen cosas raras. Esto está muy bien demostrado por las siguientes expresiones:

```
console.log(8 * null)
// → 0
console.log("5" - 1)
// → 4
console.log("5" + 1)
// → 51
console.log("five" * 2)
// → NaN
console.log(false == 0)
// → true
```

Cuando un operador se aplica a un tipo de valor "incorrecto", JavaScript convertirá silenciosamente ese valor al tipo que necesita, utilizando un conjunto de reglas que a menudo no son lo que usted desea o espera. Esto se llama _ coerción de tipo _. El `null` en la primera expresión se convierte en `0`, y `"5"` en la segunda expresión se convierte en `5` (de cadena a número). Sin embargo, en la tercera expresión, `+` intenta la concatenación de cadenas antes de la suma numérica, por lo que `1` se convierte en `"1"` (de número a cadena).

Cuando algo que no concuerda con un número de una manera obvia (como `" five "` o `undefined`) se convierte en un número, se obtiene el valor ` NaN`. Las operaciones aritméticas adicionales en `NaN` continúan produciendo` NaN`, por lo que si encuentra uno  de estos en un lugar inesperado, busque conversiones de tipo accidentales.

Al comparar valores del mismo tipo usando `==`, el resultado es fácil de predecir: debe ser verdadero cuando ambos valores son los mismos, excepto en el caso de `NaN`. Pero cuando los tipos difieren, JavaScript usa un conjunto de reglas complicado y confuso para determinar qué hacer. En la mayoría de los casos, solo intenta convertir uno de los valores al tipo del otro valor. Sin embargo, cuando hay un  `null` o un ` undefined`  en cualquier lado del operador, se produce verdadero solo si ambos lados son  `null` o` undefined`.
```
console.log(null == undefined);
// → true
console.log(null == 0);
// → false
```

Este comportamiento a menudo es útil. Cuando desee probar si un valor tiene un valor real en lugar de `null` o` undefined`, puede compararlo con `null` con el operador` == ` (o`! = `).

Pero, ¿y si quieres probar si algo tiene precisamente el valor `false`? Las expresiones como `0 == false` y` "" == false` también son ciertas debido a la conversión de tipo automática. Cuando _no_ quieres que suceda ninguna conversión de tipo, hay dos operadores adicionales: `===` y `! ==`. La primera prueba si un valor es _exactamente_ igual que el, y el segundo prueba si no es exactamente igual que el otro. Entonces `" "=== falso` es falso como se esperaba.

Recomiendo usar los operadores de comparación de tres caracteres de forma defensiva para evitar que las conversiones de tipo inesperadas te hagan equivocar. Pero cuando esté seguro de que los tipos en ambos lados son iguales, no hay problema con el uso de los operadores más cortos.

### Cortocircuito de operadores lógicos

Los operadores lógicos `&&` y `||` manejan valores de diferentes tipos de una manera peculiar. Convertirán el valor del lado izquierdo al tipo booleano para decidir qué hacer, pero según el operador y el resultado de esa conversión, devolverán el valor _original_ izquierdo o el valor derecho.

El operador `||`, por ejemplo, devolverá el valor a su izquierda cuando este se pueda convertir en verdadero y devolverá el valor a su derecha en caso contrario. Esto tiene el efecto esperado cuando los valores son booleanos y hace algo análogo con valores de otros tipos.

```
console.log(null || "user")
// → user
console.log("Agnes" || "user")
// → Agnes
```

Podemos utilizar esta funcionalidad como una forma de llegar a un valor predeterminado. Si tiene un valor que podría estar vacío, puede poner `||` después de él con un valor de reemplazo. Si el valor inicial se puede convertir en falso, obtendrá el valor de reemplazo en su lugar. Las reglas para convertir cadenas y números a valores booleanos indican que `0`,` NaN` y la cadena vacía (`" "`) cuentan como `false`, mientras que todos los demás valores cuentan como` true`. Entonces `0 || -1` produce `-1` y` "" || "!?" `cede` "!?" `.

El operador `&&` funciona de manera similar pero al revés. Cuando el valor a su izquierda es algo que se convierte en falso, devuelve ese valor y, de lo contrario, devuelve el valor a su derecha.

Otra propiedad importante de estos dos operadores es que la parte de su derecha se evalúa solo cuando es necesario. En el caso de `true || X`, no importa qué contenga `X`, incluso si es una parte del programa que hace algo _terrible_-el resultado será verdadero, y `X` nunca se evaluará. Lo mismo vale para `false && X`, que es falso e ignorará `X`. Esto se llama _ evaluación de cortocircuito _.

El operador condicional funciona de manera similar. Del segundo y tercer valor, solo se evalúa el que se selecciona.

## Sumario

En este capítulo examinamos cuatro tipos de valores JavaScript: números, cadenas, booleanos y valores indefinidos.

Dichos valores se crean escribiendo su nombre (`true`,` null`) o su value (`13`,` "abc" `). Puedes combinar y transformar valores con los operadores. Vimos operadores binarios para la aritmética (`+`, `-`,` * `,` / `y`% `), de concatenación de cadenas (` + `), de comparación (` == `,`! = `,` === `,`! == `,` <`,`> `,` <= `,`> = `), y de lógica (` && `,` || `), así como varios operadores unarios ( `-` para negar un número,`! `para negar lógicamente, y` typeof` para encontrar el tipo de valor) y un operador ternario (`?:`) para elegir uno de dos valores en función de un tercer valor.

Esto le proporciona la suficiente información para usar JavaScript como una calculadora de bolsillo, pero no para mucho más. El [próximo capítulo](program_structure) comenzará a juntar todas estas expresiones en programas básicos.
