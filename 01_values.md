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

Puede usar comillas simples tipograficas, comillas dobles o comillas simples rectas, siempre que las comillas al principio y al final de la cadena coincidan.

Casi cualquier cosa se puede poner entre comillas, y JavaScript creara un valor de tipo _string_. Pero algunos caracteres son más difíciles. Puedes imaginar cómo poner comillas entre comillas, puede ser difícil. _Newlines_ (el caracter que obtienes al presionar [enter]{nombre de la tecla}) se pueden incluir sin escaparlas solo cuando la cadena se entrecomilla con comillas simples (`` ` ``).

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

Hay, por supuesto, situaciones en las que desea que una barra invertida en una cadena sea solo una barra invertida, no un código especial. Si dos barras diagonales inversas se suceden, se colapsarán y solo quedará una en el valor de cadena resultante. Así es como se puede expresar la cadena "_Un carácter de nueva línea como` "` \ n` "` ._ ":

```
"A newline character is written like \"\\n\"."
```

Las cadenas de caracteres, también, tienen que modelarse como una serie de bits para poder existir dentro de la computadora. La forma en que JavaScript hace esto se basa en el estándar _Unicode_. Esta norma asigna un número a prácticamente todos los caracteres que necesites, incluidos los caracteres de griego, árabe, japonés, armenio, etc. Si tenemos un número para cada caracter, un string se puede describir con una secuencia de números.

Y eso es lo que hace JavaScript. Pero hay una complicación: la representación de JavaScript utiliza 16 bits por cada elemento de una cadena de caracteres, que puede describir hasta 2 ^ 16 ^ caracteres diferentes. Pero Unicode define más que esos caracteres, casi el doble. Por lo tanto, algunos caracteres, como muchos emoji, ocupan dos "posiciones de caracter" en las cadenas de caracteres de JavaScript. Volveremos a esto en [Chapter5](higher_order#code_units).

Las cadenas no se pueden dividir, multiplicar o restar, pero pueden usar el operador `+` en ellas. Este no suma, sino _concatena_, une dos cadenas. La siguiente línea producirá la cadena `" concatenate"`:

```
"con" + "cat" + "e" + "nate"
```

Los valores de cadena tienen una serie de funciones asociadas (_metodos_) que se pueden usar para realizar operaciones en ellas. Veremos más sobre esto en [Capítulo 4](data#methods).

Las cadenas escritas con comillas simples o dobles se comportan de manera muy similar; la única diferencia es en qué tipo de comillas necesitas escapar dentro de ellas. Las cadenas entrecomilladas, generalmente llamadas _plantillas literales_, pueden hacer algunas cosas más. Además de poder extender líneas, también pueden incrustar otros valores.

```
`half of 100 is ${100 / 2}`
```

Cuando se escribe algo en su interior `$ {}` en una cadena entrecomillada, su resultado será computado, conviertido en una cadena, e incluido en esa posición. El ejemplo produce "_half of 100 is 50_".

## Unary operators

{{index operator, "typeof operator", type}}

Not all operators are symbols. Some are written as words. One example
is the `typeof` operator, which produces a string value naming the
type of the value you give it.

```
console.log(typeof 4.5)
// → number
console.log(typeof "x")
// → string
```

We will use `console.log` in example code to indicate that we want to
see the result of evaluating something. More about that in the [next
chapter](program_structure).

The other operators shown all operated on two values, but `typeof`
takes only one. Operators that use two values are called _binary_
operators, while those that take one are called _unary_ operators. The
minus operator can be used both as a binary operator and as a unary
operator.

```
console.log(- (10 - 2))
// → -8
```

## Boolean values

It is often useful to have a value that distinguishes between only two
possibilities, like "yes" and "no" or "on" and "off". For this
purpose, JavaScript has a _Boolean_ type, which has just two values,
true and false, which are written as those words.

### Comparison

Here is one way to produce Boolean values:

```
console.log(3 > 2)
// → true
console.log(3 < 2)
// → false
```

The `>` and `<` signs are the traditional symbols for "is greater
than" and "is less than", respectively. They are binary operators.
Applying them results in a Boolean value that indicates whether they
hold true in this case.

Strings can be compared in the same way.

```
console.log("Aardvark" < "Zoroaster")
// → true
```

The way strings are ordered is roughly alphabetic but not really what
you'd expect to see in a dictionary: uppercase letters are always
"less" than lowercase ones, so `"Z" < "a"`, and nonalphabetic
characters (!, -, and so on) are also included in the ordering. When
comparing strings, JavaScript goes over the characters from left to
right, comparing the ((Unicode)) codes one by one.

Other similar operators are `>=` (greater than or equal to), `<=`
(less than or equal to), `==` (equal to), and `!=` (not equal to).

```
console.log("Itchy" != "Scratchy")
// → true
console.log("Apple" == "Orange")
// → false
```

There is only one value in JavaScript that is not equal to itself, and
that is `NaN` ("not a number").

```
console.log(NaN == NaN)
// → false
```

`NaN` is supposed to denote the result of a nonsensical computation,
and as such, it isn't equal to the result of any _other_ nonsensical
computations.

### Logical operators

There are also some operations that can be applied to Boolean values
themselves. JavaScript supports three logical operators: _and_, _or_,
and _not_. These can be used to "reason" about Booleans.

The `&&` operator represents logical _and_. It is a binary operator,
and its result is true only if both the values given to it are true.

```
console.log(true && false)
// → false
console.log(true && true)
// → true
```

The `||` operator denotes logical _or_. It produces true if either of
the values given to it is true.

```
console.log(false || true)
// → true
console.log(false || false)
// → false
```

_Not_ is written as an exclamation mark (`!`). It is a unary operator
that flips the value given to it—`!true` produces `false`, and `!false`
gives `true`.

When mixing these Boolean operators with arithmetic and other
operators, it is not always obvious when parentheses are needed. In
practice, you can usually get by with knowing that of the operators we
have seen so far, `||` has the lowest precedence, then comes `&&`,
then the comparison operators (`>`, `==`, and so on), and then the
rest. This order has been chosen such that, in typical expressions
like the following one, as few parentheses as possible are necessary:

```
1 + 1 == 2 && 10 * 10 > 50
```

The last logical operator I will discuss is not unary, not binary, but
_ternary_, operating on three values. It is written with a question
mark and a colon, like this:

```
console.log(true ? 1 : 2);
// → 1
console.log(false ? 1 : 2);
// → 2
```

This one is called the _conditional_ operator (or sometimes just
the _ternary_ operator since it is the only such operator in the
language). The value on the left of the question mark "picks" which of
the other two values will come out. When it is true, it chooses the
middle value, and when it is false, it chooses the value on the right.

## Empty values

There are two special values, written `null` and `undefined`, that are
used to denote the absence of a _meaningful_ value. They are
themselves values, but they carry no information.

Many operations in the language that don't produce a meaningful value
(you'll see some later) yield `undefined` simply because they have to
yield _some_ value.

The difference in meaning between `undefined` and `null` is an accident
of JavaScript's design, and it doesn't matter most of the time. In cases
where you actually have to concern yourself with these values, I
recommend treating them as mostly interchangeable.

## Automatic type conversion

In the Introduction, I mentioned that JavaScript goes out of its way
to accept almost any program you give it, even programs that do odd
things. This is nicely demonstrated by the following expressions:

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

When an operator is applied to the "wrong" type of value, JavaScript
will quietly convert that value to the type it needs, using a set of
rules that often aren't what you want or expect. This is called
_((type coercion))_. The `null` in the first expression becomes `0`,
and the `"5"` in the second expression becomes `5` (from string to
number). Yet in the third expression, `+` tries string concatenation
before numeric addition, so the `1` is converted to `"1"` (from number
to string).

When something that doesn't map to a number in an obvious way (such as
`"five"` or `undefined`) is converted to a number, you get the value
`NaN`. Further arithmetic operations on `NaN` keep producing `NaN`, so
if you find yourself getting one of those in an unexpected place, look
for accidental type conversions.

When comparing values of the same type using `==`, the outcome is easy
to predict: you should get true when both values are the same, except
in the case of `NaN`. But when the types differ, JavaScript uses a
complicated and confusing set of rules to determine what to do. In
most cases, it just tries to convert one of the values to the other
value's type. However, when `null` or `undefined` occurs on either
side of the operator, it produces true only if both sides are one of
`null` or `undefined`.

```
console.log(null == undefined);
// → true
console.log(null == 0);
// → false
```

That behavior is often useful. When you want to test whether a value
has a real value instead of `null` or `undefined`, you can compare it
to `null` with the `==` (or `!=`) operator.

But what if you want to test whether something refers to the precise
value `false`? Expressions like `0 == false` and `"" == false` are
also true because of automatic type conversion. When you do _not_ want
any type conversions to happen, there are two additional operators:
`===` and `!==`. The first tests whether a value is _precisely_ equal
to the other, and the second tests whether it is not precisely equal.
So `"" === false` is false as expected.

I recommend using the three-character comparison operators defensively to
prevent unexpected type conversions from tripping you up. But when you're
certain the types on both sides will be the same, there is no problem with
using the shorter operators.

### Short-circuiting of logical operators

The logical operators `&&` and `||` handle values of different types
in a peculiar way. They will convert the value on their left side to
Boolean type in order to decide what to do, but depending on the
operator and the result of that conversion, they will return either the
_original_ left-hand value or the right-hand value.

The `||` operator, for example, will return the value to its left when
that can be converted to true and will return the value on its right
otherwise. This has the expected effect when the values are Boolean
and does something analogous for values of other types.

```
console.log(null || "user")
// → user
console.log("Agnes" || "user")
// → Agnes
```

We can use this functionality as a way to fall back on a default
value. If you have a value that might be empty, you can put `||` after
it with a replacement value. If the initial value can be converted to
false, you'll get the replacement instead. The rules for converting
strings and numbers to Boolean values state that `0`, `NaN`, and the
empty string (`""`) count as `false`, while all the other values count
as `true`. So `0 || -1` produces `-1`, and `"" || "!?"` yields `"!?"`.

The `&&` operator works similarly but the other way around. When the
value to its left is something that converts to false, it returns that
value, and otherwise it returns the value on its right.

Another important property of these two operators is that the part to
their right is evaluated only when necessary. In the case of `true ||
X`, no matter what `X` is—even if it's a piece of program that does
something _terrible_—the result will be true, and `X` is never
evaluated. The same goes for `false && X`, which is false and will
ignore `X`. This is called _((short-circuit evaluation))_.

The conditional operator works in a similar way. Of the second and
third values, only the one that is selected is evaluated.

## Summary

We looked at four types of JavaScript values in this chapter: numbers,
strings, Booleans, and undefined values.

Such values are created by typing in their name (`true`, `null`) or
value (`13`, `"abc"`). You can combine and transform values with
operators. We saw binary operators for arithmetic (`+`, `-`, `*`, `/`,
and `%`), string concatenation (`+`), comparison (`==`, `!=`, `===`,
`!==`, `<`, `>`, `<=`, `>=`), and logic (`&&`, `||`), as well as
several unary operators (`-` to negate a number, `!` to negate
logically, and `typeof` to find a value's type) and a ternary operator
(`?:`) to pick one of two values based on a third value.

This gives you enough information to use JavaScript as a pocket
calculator but not much more. The [next
chapter](program_structure) will start tying
these expressions together into basic programs.
