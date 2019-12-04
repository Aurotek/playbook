# Recomendaciones Para Pruebas Unitarias

## Reglas

1. NO ESCRIBIRAS CODIGO para produccion HASTA que hayas ESCRITO un TEST UNITARIO que FALLE
1. NO ESCRIBIRAS MAS de UN TEST UNITARIO que sea necesario para FALLAR, y NO COMPILAR es FALLAR
1. NO ESCRIBIRAS MAS CODIGO para produccion del NECESARIO para PASAR el TEST ACTUAL que falla
     
## Manten El Test Limpio

* Debe cambiar a medida que el codigo de produccion evolucione
* Entre mas sucio, mas dificil sera modificar
* Entre mas enredado, es mas probable que dediques mas tiempo
    
## Sin Test (caida Al Caos)

1. No podras asegurar que los cambios a una parte del sistema no rompar otros componentes
1. La cantidad de fallas se incrementaran
1. Cuando el numero de fallas no intencionadas aumente, temeras hacer nuevos cambios
    
Resultado: "un juego de serpientes y escaleras" codigo enredado y lleno de bugs... que se transforma en frustacion, y el sentimiento de que el esfuerzo de hacer testing nos ha fallado
        
    TEST PERMITE UNA DIRECCION AL CAMBIO
    
## ¿que Es Lo Que Hace A Un "test Limpio"?

Las tres eles:
* legibilidad (claridad)
* legibilidad (simpiclidad)
* legibilidad (densidad de expresion)
        
Querras decir mucho con unas pocas expresiones, en medida de lo posible
    
    EVITAR
        Evitar inundar al lector con un enjambre de detalles que deben ser
        entendidos antes de que el test tenga sentido
        
## Lenguaje Especifico Del Test

En lugar de utilizar la API para manipular el sistema, escribe un conjunto
de funciones y utilidades que utilicen la API

Las funciones/utilidades ayudaran a quienes deban leer los test despues

Refactoriza el test en formas mas expresivas y breves
    
## Estandar

El codigo para el test no necesita ser mas eficiente que el codigo para
produccion

Ya que ambos entornos tienen diferentes necesidades, hay cosas que nunca
deberias hacer en el entorno de produccion que esta perfectamente bien
en un entorno de test. Usualment esos detalles estan realcionados con
memoria o eficiencia en CPU... pero nunca con detalles de limpieza
    
## Un "assert" Por Test

Es mas facil y rapido de entender

En caso de necesitar multiples "asserts", puedes separar el test y que cada
uno de ellos tenga su "assert" particular... Aun que esto podria llevar a
duplicdad* de codigo (posibles soluciones: Template Method pattern o crear
clases separadas... lo cual parece demasiado para un detalle menor)
    
## Un Concepto Por Test
Un mejor consejo seria: minimiza el numero de "asserts" por concepto
y hacer test de un solo concepto por funcion
## F.i.r.s.t.
* **Fast**: DEBE CORRER RAPIDO... de lo contrario no correras los test frecuentemente,
    y no enncontraras problemas lo suficientemente antes para arreglarlos
    facilmente
        
* **Independent**: NO DEBERA DEPENDER DE OTRO TEST... un test no deberia preparar
        las condiciones para el siguiente test... DEBERAN CORRER EN CUALQUIER
        ORDEN
        
* **Repeatable**: DEBERAN SER REPETIBLES EN CUALQUIER ENTORNO... incluso sin red.
        si no lo son, siempre tendras una excusa del por que fallan y no tendras
        la posiblidad de correr los test cuando el entorno no este disponible
    
* **Self-Validating**: DEBE TENER UNA SALIDA BOLEANA... de lo contrario la falla
        sera subjetiva y al correr los test requerira de evaluacion manual
    
* **Timely**: DEBE SER ESCRITO ANTES QUE EL CODIGO de produccion... de lo contrario
        el codigo de produccion sera mas dificil de probar o podrias escribir
        codigo no testeable


## Conclusión

Los test preservan y mejoran la flexibilidad, mantenimiento y reutilizacion
del codigo de produccion
    
    COSAS PARA RECORDAR
        limpieza
        breve y expresivo
        inventa tu testing API que actue como lenguaje especifico
        NO PERMITAS QUE LOS TEST SE PUDRAN!!
        
        Duplicidad: 
          Algunos terminos por otros:
            DRY (don't repeat yourself)
            Once, and only once
        
    Representa un oportunidad perdida para abstraccion
    Eliminandola incrementas el vocabulario del lenguaje de tu diseño y otros
        pueden usar las facilidades que tu creaste.
        El hacer codigo se vuleve mas rapido y menos propenso a errores, por
        que has subido el nivel de abstraccion
        
    Formas obvias de duplicacion:
        Cumulos de codigo identico... Solucion: metodos simples
        Switch/Case o If/Else que aparecen una y otra vez... Solucion: polimorfismo
        Modulos que tienen algoritmos similares pero que no comparten las mismas
            lineas de codigo... Solucion: Template Method, Strategy Patterns
