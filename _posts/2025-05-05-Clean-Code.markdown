---
layout: post
title: "Clean Code"
date:   2025-05-05 20:36
categories: Nim
---

# Clean Code

## 🧼 Capítulo 1 – What Is Clean Code?

### 📘 Idea central

No todo código que funciona es buen código. El código limpio es legible, mantenible y refleja disciplina profesional. Escribirlo no es un lujo, es una obligación.

### ❓ Preguntas clave

1. ¿Qué características tiene el código limpio?

2. **¿Por qué escribir código limpio es una responsabilidad profesional?**

3. ¿Qué impacto tiene el código sucio?

4. ¿Por qué es más importante la legibilidad que la velocidad de escritura?

5. ¿Qué analogías usa el autor para transmitir la importancia del código limpio?

### 💬 Cita destacada

> **“La única forma de cumplir la deadline, la única forma de ir realmente más rápido, es mantener el código siempre lo más limpio posible.”**  
> — *Robert C. Martin*

### 🧠 Insight personal – 康青旭

> Es tan irresponsable escribir código rancio bajo presión como lo sería que un doctor no se lavara las manos por atender más rápido.  
> Es responsabilidad pura y dura del programador —da igual lo que diga el project manager.  
> El código sucio puede hacer que tu producto sea inviable en el corto o largo plazo.  
> **No escribir clean code es negligencia técnica.**

**Clean Code does one thing well.** As a good book, lines of Clean Code should be replaced by images, the abstractions of the writer's intention. Clean Code **Makes it easy** **for other people to enhance it**; Code, without tests, IS NOT CLEAN. Minimizes the number of entities (classes, methods, functions, etc.) NO DUPLICATION. Clean Code is obvious, everything you read turns out to be pretty much what you expected.

### We Are Authors

No hay forma de escribir código sin leerlo. El ratio de *Leer:Escribir* mientras programamos es 10:1 por lo que es fundamental hacer que esto sea más eficiente. Si quieres hacer el código más eficiente y sencillo de trabajar **Hazlo fácil de leer**.

### The Boy Scout Rule

Leave the codebase cleaner than you found it.  
Even small actions matter:

- Rename a variable for clarity

- Break a large function

- Eliminate a duplication

- Fix a misleading comment

## 🏷️ Capítulo 2 – Meaningful Names

### 📘 Idea central

Elegir nombres es un acto de comunicación profesional: deben expresar intención, evitar ambigüedad y reflejar claramente la función de cada elemento en el código.

---

### ❓ Preguntas clave

1. ¿Qué hace que un nombre sea "significativo"?

2. ¿Cómo evito nombres confusos, ambiguos o genéricos?

3. ¿Por qué evitar codificación y prefijos en los nombres?

4. ¿Cómo afectan los nombres a la experiencia de otros desarrolladores?

5. ¿Qué reglas y ejemplos concretos da el autor para nombrar bien?

---

### 🛠️ Principios prácticos

- Utiliza nombres que revelen la intención más allá de la función (*elapsedTimeInDays >> days >= d*).

- No usar nombres con otros significados conocidos (*hipotenusa >> hp*)

- Si llamas a algo lista, que sea una lista. No confundas!

- No uses nombres que varíen poco de uno a otro (*XYZContadorEficiente, XYZSumadorEficiente*).

- Evitar palabras innecesarias y/o faltas de ortografía solo para que compile.

- No hacer métodos o variables con nombres parecidos que no digan nada (*getActiveAccount(); getActiveAccounts();*).

- Usa nombres pronunciables y que sean fáciles de buscar (y rellenar para el IDE).

- El mental mapping es una falta de profesionalidad.

- Las clases y objetos deben ser sustantivos o frases atómicas (*Cliente, ProcesadorDirecciones*).

- Los métodos deben ser nombrados por sus *get *y *set.*

- *No usar nombres chistosos ni dobles sentidos, nada expresamente cultural.*

    - Intenta mantener el lenguaje dentro del dominio de la tarea (nombres matemáticos, programación → dentro del dominio).

- *Una palabra por concepto: si contador en general lo usas para un tipo de tarea específica, al agregar algo distinto varía la palabra para diferenciar.*

---

### 💬 Citas destacadas

> **“*It will pay off in the short term and continue to pay in the long run.*”**  
> — *Robert C. Martin*

---

### 🧠 Insight personal – 康青旭

> *Este tipo de reglas parecen banales a primera vista, incluso obvias, pero son muy sencillas de identificar cuándo el código leído no es el de uno mismo. Tendemos a fácilmente no darnos cuenta de la ausencia de esto en nuestros propios programas pero es abrir código de alguien más (o algo propio antiguo) y todo salta a la vista.*

## 🔧 Capítulo 3 – Functions

### 📘 Idea central

Las funciones limpias son pequeñas, expresivas y enfocadas en una única responsabilidad.

---

### ❓ Preguntas clave

1. ¿Qué define una buena función?

2. ¿Cuál es el tamaño ideal de una función y por qué?

3. ¿Qué tipo de nombres deben tener las funciones?

4. ¿Cómo deben estructurarse sus parámetros?

5. ¿Qué errores comunes deberíamos evitar al escribir funciones?

---

### 🛠️ Principios prácticos

- Las funciones deben ser pequeñas ¿Qué tan pequeñas? Lo más pequeñas posible.

- **Los nombres deben indicar su intención y ser descriptivos.**

    - Nombre largo y descriptivo >> Corto y enigmático.

    - Sé consistente!

    - No metas efectos secundarios, solo una función y lo que dice en el nombre.

- Estas deben ser simples, una función hace eso, **una única función**.

    - Si una función hace una única cosa, no se puede separar en secciones.

- Poca identación (idealmente 1–2)

- No mezclar niveles de abstracción!!

    - Programar en Top-Down para consistencia.

- Los *switch* suelen violar todo, evitarlos.

- Cuántos menos argumentos tu función mejor.

    - Ideal - 0

    - Bueno - 1 y 2

    - Evitar - 3

    - Injustificable - +3

- Las funciones dobles (Flag Arguments, cambian con inputs booleanos) deben separarse en dos funciones distintas.

- Crear objetos para reducir el número de argumentos de una función cuándo sea posible/necesario.

- Evitar *output arguments*, esto se hace cambiando el estado del objeto.

- Exceptions >> Error codes, evitan tener que aprenderse los códigos y son mucho más limpias de implementar.

    - Try/Catch deben ser usadas como una cosa separada de las funciones, son feas.

    - Manejar errores ES UNA COSA, por lo que esto debe ser una función en si misma y no parte de una.

- Evitar la duplicación y optimizar/refactor para eliminarla.

- **Programación estructurada:**

    - cada función y bloque → único `return`.

        - Un único `return` por función.

        - No `breaks` ni `continue` en loops

        - NUNCA usar `goto`

---

### 💬 Citas destacadas

> FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL.  
> THEY SHOULD DO IT ONLY.
> 
> — Old Advice (Tradition)

---

### 🧠 Insight personal – 康青旭

> *No es que debamos seguir esta reglas al escribir código per se, mucho menos al maquetar por primera vez nuestras ideas. Esto se debe hacer una vez las ideas estén fuera de nuestra mente y sean parte de un programa. Pensar no es escribir código, Inteligente → Tonto → Inteligente, pienso (ugly), codeo (clean), entiendo. *

## 💬 Capítulo 4 – Comments

### 📘 Idea central

*¿Cuál es el mensaje central del capítulo sobre el rol de los comentarios en el código?*

---

### ❓ Preguntas clave

1. ¿Cuándo es válido agregar un comentario?

2. ¿Qué tipos de comentarios son preferibles, y cuáles deberían evitarse?

3. ¿Qué comentarios suelen indicar que el código necesita refactor?

4. ¿Cómo afecta la presencia de comentarios desactualizados o engañosos?

5. ¿Qué alternativas existen a los comentarios para mejorar la claridad?

---

### 🛠️ Principios prácticos

- Evitá comentar código que puede expresarse mejor con nombres claros o funciones bien estructuradas.

- Preferí código que **se explique a sí mismo**.

- **Comentarios buenos**:

    - Explican una decisión compleja que no es obvia.

    - Dan contexto histórico o legal (licencias, referencias externas).

    - Guían al lector cuando el código necesariamente es críptico (por performance, por ejemplo).

    - Deben dar información concisa del código que describe.

- **Comentarios malos**:

    - Repetitivos (“sum two numbers” en una función `sum(a, b)`).

    - Desactualizados o incorrectos → **peor que no tener nada.**

    - “To-do” que se olvidan por años.

- Si algo necesita explicación: *¿puedo escribirlo mejor en vez de explicarlo?*

---

### 💬 Citas destacadas

> **“The proper use of comments is to compensate for our failure to express ourself in code.”**  
> — *Robert C. Martin*

> **“Rather than spend your time writing the comments that explain the mess you've made, spend it cleaning that mess.”**  
> — *Robert C. Martin*

---

### 🧠 Insight personal – 康青旭

> *Cuántos menos comentarios usemos mejor. Una forma de verlos es considerar el lenguaje de programación con el que estás escribiendo, en si, un lenguaje, si no eres capaz de expresarte en él mismo es tu problema, agregar comentarios 'en otro idioma' no va a hacerlo más legible. Obviamente esto no aplica a todo, hay ciertos casos dónde es necesario explicar conceptos más profundos que el código en sí (piensa en una salida específica de una condición de carrera, esto no es obvio leyendo el código normalmente y necesita ser explicado).*

## 📐 Capítulo 5 – Formatting

### 📘 Idea central

Mantener un formato consistente y visualmente eficiente no es estética, es funcionalidad: mejora la comprensión, reduce errores, y permite navegar y asociar dependencias y abstracciones con claridad inmediata.

---

### ❓ Preguntas clave

1. ¿Por qué es importante el formato visual en el código?

2. ¿Cómo afecta el formato a la legibilidad y comprensión?

3. ¿Qué principios rigen una buena organización vertical y horizontal?

4. ¿Cómo debemos estructurar archivos, clases, y funciones para que se lean bien?

5. ¿Cuáles son los errores más comunes de formato y cómo evitarlos?

---

### 🛠️ Principios prácticos

- Separar **conceptos distintos con líneas en blanco**.

- Agrupar **líneas relacionadas sin interrupciones visuales**.

- La **organización vertical** muestra dependencia y secuencia.

- La **organización horizontal** debe limitar el ancho y evitar líneas largas o con múltiples conceptos.

- Las **funciones públicas deben estar al principio** de la clase; las privadas al final (como una historia: introducción → detalles).

- Usar **convenciones consistentes** para nombres, espaciado y bloques.

- Evitar mezclas de niveles de abstracción en la misma sección visual.

- Pensar el archivo como un **documento bien estructurado**: títulos claros, párrafos lógicos, sin ruido.

- Se debe mantener una convención al trabajar en equipo.

---

### 💬 Citas destacadas

> **“Without indentation, programs would be virtually unreadable by humans.”**  
> — *Robert C. Martin*

---

### 🧠 Insight personal – 康青旭

> *Muchas de las reglas de formato, como bien se muestra en el capítulo usando estadística, son casi que inherentes de cada uno, las hacemos sin darnos cuenta siguiendo el appeal visual, el tamaño de nuestras pantallas o alguna característica del editor de texto inconscientemente. Si tuviera que señalar una regla de oro sería ponerse de acuerdo al trabajar en equipo.*

## 🧱 Capítulo 6 – Objects and Data Structures

### 📘 Idea central

La diferencia entre objetos y estructuras de datos define cómo evolucionará nuestro sistema. Objetos ocultan datos y exponen comportamiento; estructuras exponen datos y dependen de funciones externas. Elegir uno u otro no es una cuestión ideológica, sino estratégica: según qué es lo que más cambiará en el tiempo, optamos por encapsular o por exponer.

---

### ❓ Preguntas clave

1. ¿Cuál es la diferencia fundamental entre objetos y estructuras de datos?

2. ¿Por qué es importante ocultar la implementación interna de los objetos?

3. ¿Cuándo conviene usar objetos y cuándo estructuras de datos?

4. ¿Cómo afecta esta elección al diseño orientado a objetos vs. diseño procedural?

5. ¿Qué errores comunes se cometen al mezclar responsabilidades entre datos y comportamiento?

---

### 🛠️ Principios prácticos

- **Objetos** exponen comportamiento y ocultan datos.

- **Estructuras de datos** exponen datos y no tienen comportamiento.

- Usar objetos permite agregar nuevos tipos (clases) fácilmente.

- Usar estructuras permite agregar nuevas funciones fácilmente.

- Los **DTO** son estructuras válidas para transportar datos sin lógica.

- Evitá getters/setters innecesarios que rompen la encapsulación.

- La **Ley de Demeter** aplica a objetos que ocultan sus datos, no a estructuras simples.

- **Active Record** parece OO pero es una estructura: mezcla datos expuestos y funciones.

- Evitá híbridos ambiguos con lógica y datos expuestos: dificultan cualquier cambio.

- Diseñar es decidir: ¿qué vas a cambiar más seguido, funciones o estructuras?

---

### 💬 Citas destacadas

> **“Hiding implementation is not just a matter of putting a layer of functions between the variables. Hiding implementation is about abstractions!”**  
> — Robert C. Martin

> **“Procedural code makes it easy to add new functions without changing the existing data structures. OO code makes it easy to add new classes without changing existing functions.”**  
> — Robert C. Martin

---

### 🧠 Insight personal – 康青旭

> No siento una división tan marcada entre programación orientada a objetos y programación funcional. Nunca la vi como dos filosofías distintas, sino como estilos que se eligen según la situación, igual que uno aprende a usar el pluscuamperfecto sin saber que lo está usando.  
> Los lenguajes modernos, al volverse más versátiles, nos acercan a algo parecido a LISP, donde todo es una forma de transformación estructurada. En ese contexto, **la decisión importante no es qué paradigma usar, sino cómo diseñar para que el sistema respire bien a medida que crece**.

## ⚠️ Capítulo 7 – Error Handling

### 📘 Idea central

Manejar errores correctamente no es opcional: es parte del diseño. El buen manejo de errores no debe obstruir la lógica principal, ni convertir el código en un pantano ininteligible.

---

### ❓ Preguntas clave

- ¿Cómo se deben manejar los errores para no interrumpir la claridad del flujo principal?

- ¿Qué ventajas tienen las excepciones frente a los códigos de error?

- ¿Qué significa programar por contrato en el contexto del manejo de errores?

- ¿Qué errores comunes hay al capturar y propagar excepciones?

- ¿Cómo separar la lógica de negocios del manejo de errores?

---

### 🛠️ Principios prácticos

- Usá **excepciones**, no códigos de error: limpian el flujo principal.

- No atrapes excepciones si no vas a manejarlas; **propagá** hasta un nivel que sí tenga contexto.

- Evitá `try/catch` gigantescos. Capturá solo lo necesario y delegá el resto.

- No uses `return` ambiguos o silenciosos: si hay error, debe ser **claro y explícito**.

- Aplicá **programación por contrato**: si una función recibe algo inválido, debe fallar rápido (*fail fast*).

- Las funciones deben ser **atómicas**: hacer una sola cosa y fallar limpiamente si no pueden.

- El código de manejo de errores debería estar **separado visual y conceptualmente** del flujo principal.

- Asumí que el sistema va a fallar y **diseñá para ese escenario**.

- Evitá retornar y pasar `null` siempre que sea posible.

- ✅ *Las checked exceptions son aquellas que el compilador te obliga a manejar manualmente. Hoy en día, la mayoría de lenguajes modernos las evitan.*

---

### 💬 Citas destacadas

> **“…the rational approach is to forbid passing null by default. When you do, you can code with the knowledge that a null in an argument list is an indication of a problem, and end up with far fewer careless mistakes.”**  
> — Robert C. Martin

---

### 🧠 Insight personal – 康青旭

> El manejo de excepciones debe pensarse antes de escribir el código, usando **exclusivamente excepciones en lugar de códigos de retorno**. Chequear si te pasan `null` es un síntoma de mal diseño. Sí, puede revisarse internamente como mecanismo de defensa, pero no debe formar parte del contrato de tus funciones. Lo más racional es simplemente **evitar el uso de `null` por completo**.

## 🧱 Capítulo 8 – Boundaries

### 📘 Idea central

Las fronteras (boundaries) entre tu código y librerías externas son inevitables, pero deben ser controladas cuidadosamente. El código limpio minimiza el acoplamiento y encapsula dependencias externas.

---

### ❓ Preguntas clave

- ¿Qué significa establecer un "boundary" en software?

- ¿Por qué es riesgoso acoplarse directamente a librerías o frameworks externos?

- ¿Cómo podés proteger tu código de futuros cambios en dependencias?

- ¿Qué técnicas propone el capítulo para controlar este acoplamiento?

- ¿Qué rol cumplen los tests y los adaptadores en este contexto?

---

### 🛠️ Principios prácticos

- Protegé tu código del cambio encapsulando las dependencias externas.

- Usá adaptadores (wrappers, interfaces, capas intermedias) para desacoplar.

- No dejes que el framework invada tu dominio; tu app debe controlar al framework, no al revés.

- Explorá librerías en "playgrounds", no en producción.

- Mantené bajo control las APIs externas para que no afecten tu arquitectura.

- Considerá que una dependencia externa es código volátil: tratala como si fuera una zona radiactiva.

- Si una API aún no existe, **definí tu propia interfaz como si ya existiera**. Después adaptás.

---

### 💬 Citas destacadas

> “Interesting things happen at boundaries. Change is one of those things. Good software designs accommodate change without huge investments and rework.”  
> — Robert C. Martin

---

### 🧠 Insight personal – 康青旭

> Las librerías son herramientas, no los cimientos. Si las ponés en el centro de tu diseño, terminarás atando a tu sistema a algo que no puedes controlar.  
> Hay que **poner límites claros**: haz que tu código hable con una interfaz propia y no directamente con la dependencia externa.  
> Eso nos permite trabajar sin que la API exista, testear y adaptarte fácilmente al cambio.  
> **No escribas tu sistema alrededor del framework. Escribí tu sistema, y adaptá el framework a tus necesidades.**

## 🧪 Capítulo 9 – Unit Tests

### 📘 Idea central

*Los tests no solo verifican que el código funcione: son parte del diseño. Un buen test guía la estructura del código, previene el miedo al cambio y asegura que podamos avanzar sin romper lo ya construido.*

---

### ❓ Preguntas clave

- ¿Qué define a un buen test?

- ¿Qué significa que un test sea legible y expresivo?

- ¿Por qué los tests deben ser rápidos y confiables?

- ¿Cómo ayudan los tests a mantener el diseño limpio?

- ¿Qué pasa cuando el código de test se vuelve difícil de mantener?

---

### 🛠️ Principios prácticos

- Usá el acrónimo **F.I.R.S.T.**:

    - **Fast**: deben correr rápido.

    - **Independent**: no deben depender de otros tests.

    - **Repeatable**: deben dar siempre el mismo resultado.

    - **Self-validating**: deben decir si pasaron o fallaron sin inspección manual.

    - **Timely**: deben escribirse justo antes del código de producción.

- Mantené los tests **tan limpios como el código de producción**.

- Si no podés testear algo fácilmente, eso es una señal de mal diseño.

- Evitá setups complicados: si preparar el entorno del test es difícil, tu arquitectura probablemente lo sea también.

- Un test sucio contamina todo el sistema: refactorizalo igual que cualquier otra parte.

---

### 💬 Citas destacadas

> *Agregá aquí las frases más fuertes del capítulo.*

---

### 🧠 Insight personal – 康青旭

> *¿Cómo cambió tu visión del testing este capítulo? ¿Tenés experiencia con tests que se volvieron una carga? ¿Qué vas a aplicar a partir de ahora?*

