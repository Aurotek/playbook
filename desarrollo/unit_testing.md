# Recomendaciones para pruebas unitarias

## Reglas

1. NO ESCRIBIRÁS CÓDIGO para producción HASTA que hayas ESCRITO un TEST UNITARIO que FALLE.
1. NO ESCRIBIRÁS MÁS de UN TEST UNITARIO que sea necesario para FALLAR, y NO COMPILAR es FALLAR.
1. NO ESCRIBIRÁS MÁS CÓDIGO para producción del NECESARIO para PASAR el TEST ACTUAL que falla.
     
## Mantén el test limpio

* Debe cambiar a medida que el código de producción evolucione.
* Entre más sucio, más difícil será modificar.
* Entre más enredado, es más probable que dediques más tiempo.
    
## Sin Test (Caída al caos)

1. No podrás asegurar que los cambios a una parte del sistema no romperá otros componentes.
1. La cantidad de fallas se incrementarán.
1. Cuando el número de fallas no intencionadas aumente, temerás hacer nuevos cambios.
    
Resultado: "Un juego de serpientes y escaleras" código enredado y lleno de bugs... que se transforma en frustración, y el sentimiento de que el esfuerzo de hacer testing nos ha fallado.
        
    TEST PERMITE UNA DIRECCIÓN AL CAMBIO
    
## ¿Qué hace a un "Test Limpio"?

Las tres eles:
* Legibilidad (claridad)
* Legibilidad (simplicidad)
* Legibilidad (densidad de expresión)
        
Querrás decir mucho con unas pocas expresiones, en medida de lo posible.
    
    EVITAR
        Evitar inundar al lector con un enjambre de detalles que deben ser
        entendidos antes de que el test tenga sentido.
        
## Lenguaje específico del test

En lugar de utilizar la API para manipular el sistema, escribe un conjunto
de funciones y utilidades que utilicen la API.

Las funciones/utilidades ayudarán a quienes deban leer los test después.

Refactoriza el test en formas más expresivas y breves.
    
## Estándar

El código para el test no necesita ser más eficiente que el código para
producción.

Ya que ambos entornos tienen diferentes necesidades, hay cosas que nunca
deberías hacer en el entorno de producción que esta perfectamente bien
en un entorno de test. Usualmente esos detalles están relacionados con
memoria o eficiencia en CPU... pero nunca con detalles de limpieza.
    
## Un "assert" por Test

Es más fácil y rápido de entender.

En caso de necesitar múltiples "asserts", puedes separar el test y que cada
uno de ellos tenga su "assert" particular... Aunque esto podría llevar a
duplicidad* de código (posibles soluciones: Template Method pattern o crear
clases separadas... lo cual parece demasiado para un detalle menor).
    
## Un concepto por Test
Un mejor consejo seria: minimiza el número de "asserts" por concepto
y hacer test de un solo concepto por función.

## F.i.r.s.t.
* **Fast**: DEBE CORRER RÁPIDO... de lo contrario no correrás los test frecuentemente,
    y no encontrarás problemas lo suficientemente antes para arreglarlos
    fácilmente.
        
* **Independent**: NO DEBERÁ DEPENDER DE OTRO TEST... un test no debería preparar
        las condiciones para el siguiente test... DEBERÁN CORRER EN CUALQUIER
        ORDEN.
        
* **Repeatable**: DEBERÁN SER REPETIBLES EN CUALQUIER ENTORNO... incluso sin red.
        si no lo son, siempre tendrás una excusa del por que fallan y no tendrás
        la posibilidad de correr los test cuando el entorno no esté disponible.
    
* **Self-Validating**: DEBE TENER UNA SALIDA BOOLEANA... de lo contrario la falla
        será subjetiva y al correr los test requerirá de evaluación manual.
    
* **Timely**: DEBE SER ESCRITO ANTES QUE EL CÓDIGO de producción... de lo contrario
        el código de producción será más difícil de probar o podrías escribir
        código no testeable


## Conclusión

Los test preservan y mejoran la flexibilidad, mantenimiento y reutilización
del código de producción.
    
    COSAS PARA RECORDAR
        Limpieza
        Breve y expresivo
        Inventa tu testing API que actúe como lenguaje específico
        ¡NO PERMITAS QUE LOS TEST SE PUDRAN!
        
        Duplicidad: 
          Algunos términos por otros:
            DRY (don't repeat yourself)
            Once, and only once
        
    Representa una oportunidad perdida para abstracción
    Eliminándola incrementas el vocabulario del lenguaje de tu diseño y otros
        pueden usar las facilidades que tú creaste.
        El hacer código se vuelve más rápido y menos propenso a errores, por
        que has subido el nivel de abstracción.
        
    Formas obvias de duplicación:
        Cúmulos de código idéntico... Solución: métodos simples
        Switch/Case o If/Else que aparecen una y otra vez... Solución: polimorfismo
        Módulos que tienen algoritmos similares pero que no comparten las mismas
            líneas de código... Solución: Template Method, Strategy Patterns
