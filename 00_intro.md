{{meta {load_files: ["code/intro.js"]}}}

# Introducción

{{quote {author: "Ellen Ullman", title: "Close to the Machine: Technophilia and its Discontents", chapter: true}

Pensamos que estamos creando un sistema para nuestros propios fines. Pensamos que lo estamos haciendo a nuestra imagen ... Pero las computadoras no son realmente como nosotros. Es una proyección de una parte muy delgada de nosotros mismos: esa parte dedicada a la lógica, el orden, la regla y la claridad.

quote}}

{{figure {url: "img/chapter_picture_00.jpg", alt: "Picture of a screwdriver and a circuit board", chapter: "framed"}}}

Este libro trata de como programar una computadora. Las computadoras son tan comunes como los destornilladores hoy en día, pero un poco más complejas, y hacer que hagan lo que tu quieres que hagan no es siempre tan facil.

Si el cometido que tiene para su computadora es una tarea común y conocida, como ver su correo electrónico o actuar como una calculadora, puede abrir la aplicación correspondiente y ponerse a trabajar. Pero para tareas únicas o no resueltas, probablemente no haya ninguna aplicación.

Ahí es donde la programación puede entrar. _Programar_ es el acto de construir un _programa_ -- un conjunto de instrucciones precisas que le dicen a la computadora qué hacer. Debido a que las computadoras son bestias tontas y pedantes, la programación es fundamentalmente tediosa y frustrante.

Afortunadamente, si puede superar ese hecho, y tal vez incluso disfrutar del rigor de pensar en términos en los que las máquinas tontas pueden manejar, la programación puede ser gratificante. Te permite hacer cosas en segundos que tardarian una __eternidad__ hechas a mano. Es una forma de hacer que su ordenador haga cosas que antes no podía hacer. Y proporciona un maravilloso ejercicio de pensamiento abstracto.

La mayoría de programas se realiza con lenguajes de programación. Un lenguaje de programación es un lenguaje construido artificialmente utilizado para instruir a las computadoras. Es interesante que la forma más efectiva en que nos hemos encontrado para comunicarnos con una computadora se deba a la forma en que nos comunicamos entre nosotros. Al igual que los idiomas humanos, los lenguajes de computadora permiten que las palabras y frases se combinen de nuevas maneras, lo que permite expresar conceptos siempre nuevos.

Por un lado las interfaces basadas en el lenguaje, como las de 'Prompt BASIC y DOS' de 1980 y 1990, fueron el  método principal para interactuar con las computadoras. En su mayoría, han sido reemplazados por interfaces visuales, que son más fáciles de aprender pero ofrecen menos libertad. Los lenguajes de computadora todavía están allí, si sabes dónde mirar. Uno de estos lenguajes, JavaScript, está integrado en todas los navegador web modernos y, por lo tanto, está disponible en casi todos los dispositivos.

Este libro tratará de familiarizarte lo mas posible con este lenguaje para hacer cosas útiles y divertidas con él.

## Sobre la programación

Además de explicar JavaScript, presentaré los principios básicos de la programación. La programación, resulta que, es difícil. Las reglas fundamentales son simples y claras, pero los programas creados sobre estas reglas tienden a ser lo suficientemente complejos como para introducir sus propias reglas y complejidades. Estás construyendo tu propio laberinto, de alguna manera, y podrías perderte en él.

Habrá momentos en que leer este libro te siente terriblemente frustrante. Si eres nuevo en la programación, habrá mucho material nuevo para digerir. Gran parte de este material se __combinará__ de formas que requiera que hagas conexiones adicionales.

Depende de ti que hagas el esfuerzo necesario. Cuando estés luchando por seguir el libro, y no llegues a ninguna conclusión sobre tus propias capacidades. Estás bien, solo tienes que seguir así. Tómese un descanso, vuelva a leer algunas materias y asegúrese de leer y comprender los programas de ejemplo y los ejercicios. Aprender es un trabajo duro, pero todo lo que aprenda es suyo y facilitará el aprendizaje posterior.

{{quote {author: "Ursula K. Le Guin", title: "The Left Hand of Darkness"}

Cuando la acción no sea rentable, recopile información; cuando la información no sea rentable, duerma.

quote}}

Un programa es muchas cosas. Es una pieza de texto escrita por un programador, es la fuerza directriz que hace que la computadora haga lo que hace, son datos en la memoria de la computadora, y sin embargo, controla las acciones realizadas en esta misma memoria. Las analogías que intentan comparar los programas con objetos con los que estamos familiarizados tienden a fallar. Una adaptación superficial es la de una máquina -- muchas porciones separadas tienden a estar involucradas, y para hacer funcionar todo, debemos considerar las formas en que estas partes se interconectan y contribuyen a la operación del todo.

Un ordenador es una máquina física que actúa como anfitrion para estas máquinas virtuales. Las computadoras mismas solo pueden hacer cosas estúpidamente sencillas. La razón por la que son tan útiles es que hacen estas cosas a un nivel increíblemente alto de velocidad. Un programa puede combinar ingeniosamente una enorme cantidad de estas acciones simples para hacer cosas muy complicadas.

Un programa es una edificación de pensamientos. No cuesta construir, no pesa, y crece fácilmente bajo nuestras manos.

Pero sin cuidado, el tamaño y complejidad de un programa  crecerá fuera de control, confundiendo incluso a la persona que lo creó. Mantener los programas bajo control es el problema principal de la programación. Cuando un programa funciona, es hermoso. El arte de la programación es la habilidad de controlar la complejidad. El gran programa es moderado, hecho simple en su complejidad.

Algunos programadores creen que esta complejidad se maneja mejor utilizando solo un pequeño conjunto de técnicas, bien entendidas, en sus programas. Han compuesto reglas estrictas ("mejores prácticas") que prescriben la forma  que los programas deberían tener y permanecen celosamente dentro de su pequeña zona segura.

Esto no solo es aburrido, es ineficaz. Los nuevos problemas a menudo requieren nuevas soluciones. El campo de la programación es joven y aún está desarrollandose rápidamente, y es lo suficientemente variado para tener espacio para enfoques totalmente diferentes. Hay muchos errores terribles que cometer en el diseño del programa, y debes continuar y cometerlos para que los entiendas. El sentido de cómo se ve un buen programa se desarrolla en la práctica, no se aprende de una lista de reglas.

## Por qué el lenguaje importa (cuestiones lingüísticas)


Al principio, en los origenes de la informática, no había lenguajes de programación. Los programas se veían así:

```
{lang: null}
00110001 00000000 00000000
00110001 00000001 00000001
00110011 00000001 00000010
01010001 00001011 00000010
00100010 00000010 00001000
01000011 00000001 00000000
01000001 00000001 00000001
00010000 00000010 00000000
01100010 00000000 00000000
```

Este es un programa para sumar los números del 1 al 10 e imprimir el resultado: `1 + 2 + ... + 10 = 55`. Podría funcionar hipotéticamente, en una maquina sencilla. Para programar las primeras computadoras, era necesario configurar grandes matrices de interruptores en la posición correcta o hacer agujeros en targetas perforadas y alimentarlas a la computadora. Probablemente puedas imaginar lo tedioso y propenso a errores que fue este procedimiento. Incluso escribir programas simples requería mucha astucia y disciplina. Los complejos eran casi inconcebibles.

Por supuesto, ingresar manualmente estos patrones cecretos de bits (unos y ceros) le dio al programador una profunda sensación de ser un poderoso mago. Y eso tiene que valer algo en términos de satisfacción laboral.

Cada línea del programa anterior contiene una sola instrucción. Podría escribirse en español así:

 1. Almacene el número 0 en la ubicación de la memoria 0.
 2. Almacene el número 1 en la ubicación de la memoria 1.
 3. Almacene el valor de ubicación de memoria 1 en ubicación de memoria 2.
 4. Reste 11 del valor almacenado en la ubicación de memoria 2.
 5. Si el valor en la ubicación de la memoria 2 es el número 0, continúe con la instrucción 9.
 6. Agregue el valor de la ubicación de memoria 1 a la ubicación de memoria 0.
 7. Agregue 1 al valor de la ubicación de memoria 1.
 8. Continuar con la instrucción 3.
 9. Muestra el valor de la ubicación de memoria 0.

Aunque esto ya es más legible que la sopa de bits, todavía es bastante oscuro. Usar nombres en lugar de números para las instrucciones y ubicaciones de memoria ayuda.

```
{lang: "text/plain"}
 Set “total” to 0.
 Set “count” to 1.
[loop]
 Set “compare” to “count”.
 Subtract 11 from “compare”.
 If “compare” is zero, continue at [end].
 Add “count” to “total”.
 Add 1 to “count”.
 Continue at [loop].
[end]
 Output “total”.
 ```

¿Puedes ver cómo funciona el programa en este punto? Las primeras dos líneas asignan un valor inicial a dos posiciones de memoria: se usará `total`para almacenar el resultado del cálculo, y `count` hará un seguimiento del número que estamos mirando actualmente. Las líneas que usan `compare` son probablemente las más extrañas. El programa quiere ver si `count` es igual a 11 para decidir si detiene la ejecución. Debido a que nuestra hipotética máquina es bastante primitiva, sólo se puede comprobar si un número es cero y tomar una decisión en base a eso. Por lo tanto, utiliza la ubicación de memoria etiquetada como `comparar` para calcular el valor de` count - 11` y toma una decisión basada en ese valor. Las siguientes dos líneas agregan el valor de `count` al resultado y
Incremente `count` en 1 cada vez que el programa haya decidido que` count`
todavía no es 11.

Aquí está el mismo programa en JavaScript:

```
let total = 0, count = 1;
while (count <= 10) {
  total += count;
  count += 1;
}
console.log(total);
// → 55
```

Esta versión nos da algunas mejoras más. Lo más importante, es que no es necesario especificar la forma en que queremos que el programa salte hacia adelante o hacia detras. La estructura `while` se ocupa de eso. Continúa ejecutando el bloque (envuelto en llaves) debajo de él, siempre que se cumpla la condición que se le dio. Esa condición es `count <= 10`, lo que significa que '_count_ es menor o igual a 10' '. Ya no tenemos que crear un valor temporal y compararlo con cero, que era solo un detalle sin interés. Parte del poder de los lenguajes de programación es que pueden ocuparse de detalles poco interesantes para nosotros.

Al final del programa, después de que `while` haya terminado,la operación `console.log` se encarga de mostrar el resultado.

Finalmente, aquí está el aspecto que podría tener el programa si tenemos las operaciones convenientes `range` y` sum` disponibles, que crean respectivamente una colección de números dentro de un rango y calculan la suma de una colección de números

```
{startCode: true}
console.log(sum(range(1, 10)));
// → 55
```

La moraleja de esta historia es que el mismo programa se puede expresar en formas largas y cortas, ilegibles y legibles. La primera versión del programa era extremadamente oscura, mientras que esta última es casi inglesa: `log` la` suma` del `rango` de números del 1 al 10. (Veremos en [capítulos posteriores](datos) cómo definir operaciones como `sum` y `range`).

Un buen lenguaje de programación ayuda al programador permitiéndole decir en un nivel superior que acciones debe realizar la computadora. Ayuda a omitir detalles, proporciona bloques de construcción convenientes (como `while` y` console.log`), le permite definir sus propios bloques de construcción (como `sum` y` range`), y hace que esos bloques sean fáciles de componer.

## Qué es JavaScript?

JavaScript fue introducido en 1995 como una forma de agregar programas a las páginas web en Netscape Navigator. Desde entonces, el lenguaje ha sido adoptado por todos los demas navegadores web gráficos. Ha hecho posibles aplicaciones web modernas, aplicaciones con las que puede interactuar directamente sin tener que volver a cargar una página en cada acción. JavaScript también se utiliza en sitios web más tradicionales para proporcionar diversas formas de interactividad y habilidad.

Es importante tener en cuenta que JavaScript no tiene casi nada que ver con el lenguaje de programación llamado Java. La similaridad del nombre se inspiró en consideraciones de marketing en lugar del buen juicio. Cuando se introdujo JavaScript, el lenguaje Java estaba siendo muy comercializado y estaba ganando popularidad. Alguien pensó que era una buena idea tratar de seguir este éxito. Ahora estamos atrapados con el nombre.

Después de su adopción fuera de Netscape, se escribió un documento estándar para describir la forma en que debería funcionar el lenguaje JavaScript, de modo que los diferentes componentes de software que afirmaban que admitían JavaScript hablasen en realidad el mismo idioma. Esto se conoce como el estándar ECMAScript, después de que la organización Ecma International hiciese la estandarización. En la práctica, los términos ECMAScript y JavaScript se pueden usar indistintamente, son dos nombres para el mismo lenguaje.

Hay quienes dirán cosas _terribles_ sobre JavaScript. Muchas de las cuales son verdaderas. Cuando me pidieron que escribiera algo en JavaScript por primera vez, rápidamente comencé a despreciarlo. Aceptaba casi cualquier cosa que escribía, pero las interpretaba de una manera completamente diferente de lo que yo quería. Esto tuvo mucho que ver con el hecho de que no tenía ni idea de lo qué estaba haciendo, por supuesto, pero hay un problema real: JavaScript es ridículamente liberal en todo lo que permite. La idea detrás de este diseño fue que facilitaría la programación en JavaScript a los principiantes. En realidad, en general dificulta la búsqueda de problemas en sus programas porque el sistema no los señalará.

Sin embargo, esta flexibilidad también tiene sus ventajas. Deja espacio para muchas técnicas que son imposibles en lenguajes más rígidos, y como verá (por ejemplo en [Capítulo 10](modules)), puede usarse para superar algunas de las deficiencias de JavaScript. Después de ((aprender)) el lenguaje correctamente y de trabajar con él por un tiempo, he aprendido realmente a _querer_ a JavaScript.

Han habido varias versiones de JavaScript. la versión 3 de ECMAScript  fue la versión más ampliamente soportada en el momento del ascenso del predominio de JavaScript, aproximadamente entre 2000 y 2010. Durante este tiempo, se estaba trabajando en una ambiciosa versión 4, que planificaba una serie de mejoras  y extensiones radicales del lenguaje. Cambiar un lenguaje vivo y ampliamente utilizado de manera tan radical resultó ser políticamente difícil, y el trabajo sobre la versión 4 fue abandonado en 2008, lo que llevó a una versión 5 mucho menos ambiciosa, que hizo solo algunas mejoras incontrovertibles, que salieron en 2009. Luego en 2015 salió la versión 6, una importante actualización que incluía algunas de las ideas planificadas para la versión 4. Desde entonces, hemos tenido nuevas pequeñas actualizaciones cada año.

El hecho de que el lenguaje esté evolucionando significa que los navegadores deben mantenerse al día constantemente, y si está usando un navegador más antiguo, es posible que no admita todas las características. Los diseñadores de lenguajes tienen cuidado de no realizar ningún cambio que pueda romper los programas existentes, por lo que los navegadores nuevos aún pueden ejecutar programas antiguos. En este libro, estoy usando la versión 2017 de JavaScript.

Los navegadores web no son las únicas plataformas en las que se usa JavaScript. Algunas bases de datos, como MongoDB y CouchDB, usan JavaScript como lenguaje de scripting y consulta. Varias plataformas para programación de escritorio y servidor, la más notable el proyecto ((Node.js)) (el tema del [Capítulo 20](node)), proporcionan un entorno para programar JavaScript fuera del navegador.

## El código y qué hacer con él

El _código_ es el texto que compone los programas. La mayoría de los capítulos de este libro contienen bastante código. Creo que leer código y escribir código son partes indispensables del aprendizaje para programar. Intente no solo echar un vistazo a los ejemplos, léalos atentamente y entiéndalos.Este puede ser lento y confuso al principio, pero le prometo que lo entenderá rápidamente. Lo mismo ocurre con los ejercicios. No asuma que los comprende hasta que haya escrito una solución funcional.

Te recomiendo que pruebes las soluciones de los ejercicios en un intérprete real de JavaScript. De esta forma, recibirás un feedback inmediato sobre si lo que estás haciendo está funcionando y, espero, que quieras experimentar e ir más allá de los ejercicios.

{{if interactive

Al leer este libro en un navegador, puede editar (y ejecutar) todos los ejemplos de programas haciendo clic sobre ellos.

if}}

{{if book

La forma más fácil de ejecutar el código de los ejemplos del libro y experimentar con él es buscarlo en la versión onlíne del libro en [_https: //eloquentjavascript.net_](https://eloquentjavascript.net/). Allí, puede hacer clic en cualquier ejemplo de código para editarlo y ejecutarlo, y para ver el resultado que produce. Para trabajar en los ejercicios, ve a [_https: //eloquentjavascript.net/code_](https://eloquentjavascript.net/code), que proporciona un código para comenzar cada ejercicio de codificación y le permite ver las soluciones.

if}}

Si desea ejecutar los programas definidos en este libro fuera del sitio web del libro, se necesitará cierto cuidado. Muchos ejemplos se sostienen por sí solos y deberían funcionar en cualquier entorno de JavaScript. Pero el código de los últimos capítulos  a menudo se escriben para entornos específicos (el navegador o Node.js) y solo se puede ejecutar allí. Además, muchos capítulos definen programas enormes, y las piezas de código que aparecen en ellos dependen unas de otras o de archivos externos. En [sandbox](https://eloquentjavascript.net/code) del sitio web, se proporcionan enlaces a archivos Zip que contienen todos los scripts y archivos de datos necesarios para ejecutar el código de un capítulo determinado.

## Descripción del libro

Este libro contiene aproximadamente tres partes. Los primeros 12 capítulos hablan del lenguaje JavaScript. Los siguientes siete capítulos tratan sobre navegadores web  y la forma en que JavaScript se usa para programarlos. Finalmente, dos capítulos están dedicados a Node.js, otro entorno para programar en JavaScript.

A lo largo del libro, hay cinco _capítulos de proyectos_, que describen programas de ejemplo más extensos para darle una idea de la programación real. En orden de aparición, trabajaremos en la construcción de un [robot de reparto](robot), un [lenguaje de programación](language), un [juego de plataforma](game), un [programa de pintura de píxel](paint) y un [ sitio web dinámico](skillsharing).

La parte del lenguaje del libro comienza con cuatro capítulos que presentan la estructura básica del lenguaje en JavaScript. Introducen [estructuras de control](program_structure) (como la palabra `while` que viste en esta introducción), [funciones](functions) (escribiendo tus propios bloques de construcción) y [estructuras de datos](data). Después de esto, podrás escribir programas básicos. A continuación, los capítulos [5](higher_order) y [6](object) introducen técnicas para usar funciones y objetos para escribir más código _abstracto_ y mantener la complejidad bajo control.

Después de un [primer capítulo de proyecto](robot), la parte del libro sobre lenguaje continúa con capítulos sobre [manejo de errores y corrección de errores](error), [expresiones regulares](regexp) (una herramienta importante para trabajar con texto), [modularidad ](modules) (otra defensa contra la complejidad) y [programación asincrónica](async) (que trata de eventos que se toman su tiempo). El [segundo capítulo de proyecto](language) concluye la primera parte del libro.

La segunda parte, Capítulos [13]((browser) a [19](paint), describe las herramientas a las que el navegador JavaScript tiene acceso. Aprenderá a mostrar cosas en la pantalla Capítulos [14](dom) y [17] (canvas), responderá a la entrada del usuario Capítulo [15] (event) y se comunicará a través de la red Capítulo[18](http). De nuevo hay dos capítulos de proyectos en esta parte.

Después de eso, el Capítulo [20](node) describe la programación en el entorno Node.js, y el Capítulo [21](skillsharing) construye un pequeño sitio web usando esa herramienta.

{{if commercial

Finalmente, Capítulo [22](fast) describe algunas de las consideraciones que aparecen cuando se optimizan los programas JavaScript para ganar velocidad.

if}}

## Convenciones tipográficas

En este libro, el texto escrito con una fuente 'monoespaciada' representará elementos de programas, a veces son fragmentos autosuficientes y, a veces, solo se refieren a una parte de un programa. Los programas (de los cuales ya ha visto algunos) se escriben de la siguiente manera:

```
function factorial(n) {
  if (n == 0) {
    return 1;
  } else {
    return factorial(n - 1) * n;
  }
}
```

A veces, para mostrar el resultado que produce un programa, el resultado esperado se escribe después de él, con dos barras diagonales y una flecha al frente.

```
console.log(factorial(8));
// → 40320
```

Buena suerte!
