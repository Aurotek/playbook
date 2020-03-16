# Test Driven Development

## ¿Qué es TDD?

Es una disciplina que promueve el desarrollo de software con altos niveles de calidad, simplicidad de diseño y productividad del programador, mediante la utilización de una amplia gama de tipos de pruebas automáticas a lo largo de todo el ciclo de vida del software. El principio fundamental es que las pruebas se escriben antes que el software de producción y estas constituyen la especificación objetiva del mismo.

## ¿Porqué TDD?

Uno de los retos mas comunes de cualquier equipo de desarrollo es asegurarse de que el producto sea mantenible y de calidad. Por lo regular esto se resuelve contratando a un equipo de QA (*quality assurance*) que prueba las cosas antes de que se manden a producción. Aunque este es un buen primer paso está limitado por el tiempo que toma probar y que se prueben las cosas correctas. 

Mientras mas se tarde el código en QA mas nos tardamos en mandar nuestro código a producción y se puede dar el caso que el código no se puede mover hasta que pasen las pruebas de calidad.

Recordemos que nuestra mayor prioridad es satisfacer al cliente mediante entregas frecuentes de software con valor.  TDD nos ayuda a automatizar el proceso de pruebas, al asegurarnos de que todas las nuevas tienen pruebas definidas que todos pueden correr en su computadora.

## ¿Cómo?

Sabemos que hacer pruebas puede ser abrumador por tantos conceptos y términos nuevos y sobre todo por el miedo a que lo hagamos mal. 

La recomendación mas sencilla para aprender es: **Aprende a hacer pruebas escribiendo tus primeras pruebas**

Puedes basarte en pruebas existentes o apoyarte con algún compañero.

Aquí hay algunos links con información que te puede ayudar:

* [Notas sobre Unit testing](unit_testing.md)
* [TDD Guía para los no iniciados](http://artesanos.de/software/2012/02/13/tdd-como-y-porque-una-guia-para-los-no-iniciados/)
* [Curso de TDD para Laravel](https://laracasts.com/skills/testing) (existe una cuenta de Auronix para poder verlos)
* [Curso de TDD para C#](https://www.c-sharpcorner.com/article/test-driven-development-tdd-part-one/)
* [Usar NUnit en C#](https://www.youtube.com/watch?v=nOCnmr7JrSo)

## Preguntas comunes

**Hacer pruebas es muy tardado ¿Puedo saltármelas si es algo urgente?**

Esta es la excusa más común para no hacer pruebas y es muy peligrosa. Muchas veces sacrificamos calidad del código por la prisa, lo que se refleja en bugs en producción y tiempo en corregirlo, esto se multiplica mientras mas código sin pruebas haya en el proyecto ya que en cada nuevo cambio debemos asegurarnos de que no rompimos nada mas. Según varios estudios las compañías que adoptan TDD pueden reducir entre 40% y 90% la cantidad de bugs en producción.

En pocas palabras estamos invirtiendo 20% de tiempo adicional al tiempo de desarrollo inicial para reducir el tiempo de mantenimiento, debug y costos de soporte en el futuro.

**¿Cómo decido si debo hacer una prueba unitaria o una de integración?**

Las pruebas unitarias en general nos ayudan a probar una parte muy pequeña del código puede ser para asegurarnos que una función se comporte como esperamos con diferentes parámetros o para validar que maneje bien los casos especiales.

Las pruebas unitarias son en las que estamos probando mas de un módulo a la vez. por lo regular estas pruebas imitan el comportamiento de un usuario.

**¿Cómo pruebo un componente externo que no depende de mi? **
Debes diseñar tus pruebas de tal manera que puedan correr aunque estés desconectado de internet. Esto por lo regular se logra creando una clase que consuma los servicios externos y en tus tests en lugar de usar esa clase, usas un mock que no va al internet. a esta práctica se le conoce como [No pruebes lo que no es tuyo](https://www.youtube.com/watch?v=nOCnmr7JrSo)

**Ya leí todo esto y aun no se como escribir mi primer prueba. AIUDA**
Lo más probable es que te estés sobre complicado, recuerda siempre buscar lo mas [simple](https://en.wikipedia.org/wiki/KISS_principle)
Si no sabes como empezar tal vez convenga partir la prueba en pruebas mas pequeñas que sí se puedan probar

Recuerda que una prueba se debe poder escribir como una frase Given When Then. Por ejemplo


```txt
Teniendo un usuario "user1"
Cuando intento crear un usuario con el mismo nombre
Entonces me debe mostrar el error "Usuario no disponible"
```

Ya una vez que lo tengas definido convertirlo a código es más sencillo, primero prepara todo lo necesario, después ejecuta la acción o función que quieres probar y al final asegúrate que la respuesta que obtuviste era la que esperabas.
