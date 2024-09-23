# Proyecto 2 - Codificación para fuentes con memoria

## Sistemas de Comunicaciones Digitales I - 2024

### Autor: Jesus Avila

---

## Resumen

Este trabajo presenta una investigación y desarrollo en torno a la codificación para fuentes con memoria, haciendo uso de modelos de Markov y el algoritmo de compresión LZ77. El objetivo es explorar cómo la estructura de una fuente discreta de Markov puede ser aprovechada para optimizar la compresión de datos, utilizando para ello un modelo de frecuencias condicionales entre palabras. Se implementó una rutina en Python que toma como entrada un archivo de texto en formato UTF-8 y genera una tabla de frecuencias, un modelo de fuente de Markov y una implementación del algoritmo LZ77. Finalmente, se evalúa la eficiencia del algoritmo midiendo el índice de compresión logrado. Los textos utilizados para este análisis fueron descargados de la plataforma Proyecto Gutenberg.

---

## Introducción

La codificación eficiente de fuentes de información con memoria es un tema clave en la teoría de la información y las comunicaciones digitales. Mientras que fuentes sin memoria, como las cadenas de símbolos independientes, se han estudiado extensamente, fuentes con memoria, como las cadenas de Markov, presentan características más complejas y desafiantes. Estas fuentes capturan las dependencias entre símbolos, lo que abre la puerta a nuevas oportunidades para la compresión de datos.

El presente trabajo se enfoca en el estudio de las fuentes de Markov, un tipo de proceso estocástico donde la probabilidad de ocurrencia de un símbolo depende de los símbolos precedentes. A partir de esta base, se explora el concepto de entropía condicional y cómo este influye en la compresión de datos.

Para aprovechar estas propiedades, se implementa el algoritmo LZ77, que es un esquema de compresión para fuentes con memoria que funciona detectando patrones repetidos en una secuencia de símbolos. Utilizando tanto la fuente de Markov como LZ77, se busca maximizar la eficiencia en la codificación de textos reales.

---

## Metodología

### Cadena de Markov
Una cadena de Markov es una secuencia de simbolos de un alfabeto discreto finito, los cuales tienen una propabilidad de ocuerrencia condicionado al ultimo(s) simbolo que apareció.


### Fuente de Markov

Una fuente de Markov genera una secuencia de símbolos donde la probabilidad de aparición de un símbolo está condicionada por los símbolos que lo preceden. Este tipo de fuentes es útil en la compresión de datos ya que capta patrones de dependencias entre símbolos. Para nuestro modelo de fuente de Markov, se desarrolló una rutina en Python que toma un texto y genera una tabla de frecuencias condicionales para las últimas *N* palabras, donde *N* es un parámetro ajustable.

### Entropía Condicional

La Entroía condicional es un concepto que generaliza el concepto de entropía a fuentes que son "sin memoria" sino que tienen una probabilidad condicional, en este caso mide la incertidumbre en el próximo símbolo, dado un cierto símbolo acutal. 

#### Fuente de Conceptos
Gallager, R. G. (1986). Chapter 2: Information Theory. En Digital Communications (Vol. 2, pp. 25-60). New York: Cambridge University Press.

### Algoritmo LZ77

El algoritmo LZ77 es un método de compresión basado en la detección de repeticiones en una ventana deslizante sobre la secuencia de entrada. La idea clave es aprovechar las repeticiones de subcadenas en los datos, lo que lo hace ideal para fuentes con memoria, como las modeladas por procesos de Markov. Durante la compresión, el algoritmo codifica las repeticiones como una tupla \( offset, longitud \), que representa la posición y el tamaño de la secuencia repetida en la ventana.

## Resultados y Discusion

Se implementó una versión del algoritmo LZ77 en Python que toma como entrada una cadena de texto y la comprime generando una salida binaria (en unos y ceros). Durante el proceso de compresión, los literales son codificados utilizando el estándar UTF-8, lo que asegura una representación compacta de los caracteres.
La implementación no es exactamente la de (1) pero esta basada en.

(1) Gallager, R. G. (1986). Chapter 2: Information Theory. En Digital Communications (Vol. 2, pp. 25-60). New York: Cambridge University Press.

A través de las funciones:

### codifica(cadena,ventana)
    A través de  esta funcion se codifica en caracteres '1' y '0', una representacion de lo que serían los bits de una compresion a través del algoritmo lz77 del String "cadena" usando una ventana de longitud "ventana", siendo el valor de ventana la cantidad de simbolos que considera de la cadena al momento de buscar repeticiones.
    En el principio de la cadena salida, van codificados la cantidad de bits de la codificacion y la longitud de la ventana usada, la cual por eficiencia de ejecucion debe tomar valroes potencia de 2.

### decodifica(cadena)
    Devuelve la cadena original a partir del "binario" generado por la funcion anterior.

## Conclusiones

En resumén a través de la implementación se observo ue el algoritmo lz77 realiza una buena compresión cuando la cadena es larga sumada, a un longitud de ventana adecuada. Esto no significa que sea necesario que sea grande, sucesivas pruebas demuestran que ciertos valores son mas efectivos para cada cadena especifica a convertir, y determinar esta cantidad, no es trivial.



