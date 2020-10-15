# Sistemas Operativos y Redes

## Trabajo Práctico de hilos y semáforos


El trabajo práctico consiste en representar una competencia de hamburguesas. En dicha competencia, los equipos deberán armar dos hamburguesas para ganar, y para ello deberan seguir todos los pasos de la receta de hamburguesa. Algunas tareas, en particular las tareas de salar, hornear el pan y cocinar la carne, solo las puede realizar un equipo al mismo tiempo. 

La primera gran traba que encontre en el trabajo fue, como siempre, la sintaxis. Al no conocer C y haber visto muy poco código, muchas expresiones eran muy dificiles de entender.
Sumado a esta traba sintáctica, algunos conceptos como el struct o los mutex todavia no me quedaban muy claros, ademas de estar muy acostumbrado a pensar la programación puramente orientada a objectos. Para estos problemas, basicamente, busque tutoriales en youtube que explicaran detallamente todo. 

Al empezar el trabajo quise evitar a toda costa programar en el t800, ya que el visual studio code es mucho más agradable a la vista y constantemente marca errores de sintaxis o recomendaciones. Lo que no sabía era que las librerias de threads de windows no eran compatibles con las de linux. Estuve varias horas intentando descargarme las librerias o importarlas de otra forma, hasta que encontre un foro en el que hablaban del mismo problema. En este foro recomendaban usar un compilador online el cual, aunque no me debajaba testear en input y output de otros archivos, si me sirvió para ir programando todo lo demas. 

Una vez que entendia medianamente el código, hice el pseudocódigo para poder entender el "camino" que tenia que seguir la ejecución. Con esto, quedaba mucho más claro cuales eran las funciones que restringian a otras, cuales podían hacerse paralelamente y cuales necesitaban un mutex. 

Teniendo esto claro, declaré todas las funciones que representaban las diferentes acciones de la receta. Para algunas funciones, como por ejemplo la función de salar, implementé un mutex para que excluya a los demas equipos, ya que no pueden salar dos al mismo tiempo. Para otras, como mezclar, simplemente use un semaforo para indicarle al paso siguiente , en este caso la función de armar un medallon, que ya podía empezar a ejecutarse. 

Respecto a la declaración de los semaforos y variables o la inicialización de los mismos, me fui guiando por el template dado, declarando todo donde estaba comentado o bien, donde ya se habia declarado un semaforo a forma de ejemplo. 

Un problema que tuve fue que no podía ejecutar varias veces la función de "ejecutarReceta", para simular que se hacia mas de una hamburguesa. Al final, opté por un while en el main, donde se inicializan los hilos. Creo que no es la forma óptima de hacerlo, pero no quería quedarme trabado ahí y eso cumplía con la consigna. De la misma forma, tuve problemas con que cada equipo supiese cuantas hamburguesas ya hizo. Hasta donde yo entendí, la forma óptima era hacer una variable int en el struct parámetro. De esta forma, cada equipo llevaría su propia cuenta. Intenté hacer esto de varias formas pero el código no compilaba. Para solucionar esto hice algunas variables globales para llevar el conteo de los diferentes equipos y de los ganadores. No es una buena práctica abusar de las variables globales, pero me ayudó a no quedarme estancado. 

En cuanto a leer la receta en otro archivo, fue lo que mas dificultad me dio. Lo intente hacer con varios metodos que gettean cadenas de archivos, intente hacerlo con ciclos while, usando expresiones regulares pero siempre tiraba errores. Lo que pude lograr es gettear las strings, borrarles el fin de linea y asignarlos de manera hardcodeada. Esto ultimo se podria hacer de una forma mucho mas limpia con ciclos, pero no logre hacer que compilara, quizas por un error de sintaxis. 





