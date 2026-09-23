# MiniStore — Soluciones con Outer JOINs

## Consulta 1: LEFT JOIN
**¿Por qué usaste LEFT JOIN para la Consulta 1 y no INNER JOIN? ¿Qué se perdería si usaras INNER JOIN?**

En la consulta 1 se utilizó left join ya que nos queríamos dirigir y traer todos los datos de la tabla izquierda y los datos que estaban relacionados entre la tabla izquierda y derecha, evitando los datos únicos de la tabla derecha. En el caso que hubiéramos usado inner join no nos hubiera servido ya que nos traería solo los datos que se relacionan entre las 2 tablas, sin darnos los datos de la tabla izquierda, perdiendo los productos 108 (Hub USB-C) y 109 (Parlante Bluetooth) que también lo necesitábamos para resolver el ejercicio según lo que pedía la consulta 1.

## Consulta 2: RIGHT JOIN
**¿Por qué usaste RIGHT JOIN para la Consulta 2? ¿Qué tabla está a la izquierda y cuál a la derecha en tu consulta?**

En este caso utilizamos en la consulta 2 el RIGHT JOIN ya que en este ejercicio necesitábamos dirigirnos hacia los datos que se encuentran en la tabla derecha más los datos que se relacionaban con la tabla de la izquierda, evitando los datos únicos de la tabla izquierda. En nuestra consulta nuestra tabla que se encontraba a la izquierda era la de productos y la tabla de la derecha era la de ventas. Con RIGHT JOIN detecté la venta 10 con el producto_id = 999, y esto significa que también nos trajo una inconsistencia, la cual es un producto que no existe como tal en la tabla de productos, y para nuestro negocio podría surgir información falsa, errores e inconsistencias a la hora de llamar ciertos datos.

## Valores NULL en los resultados
**¿Qué representan los valores NULL en cada resultado? Explicá con un ejemplo concreto qué significa que venta_id sea NULL en la Consulta 1 y que producto_id de productos sea NULL en la Consulta 2.**

Los valores NULL no representan un dato vacío o 0, sino que significan un dato nulo, que nunca se le agregó nada a esa columna y no existe el dato. Por ejemplo, en la consulta 1, donde colocamos WHERE v.venta_id IS NULL, nos referimos y estamos llamando a los productos los cuales todavía no registran una venta de ellos (id:108, Hub USB-C 7p, id:109, Parlante Bluetooth), por lo tanto, al nunca haberse generado una venta de esos productos, el campo de venta_id va a ser nulo. En la consulta 2 podemos ver también una venta registrada donde los datos del producto nunca se colocaron, por lo tanto son nulos (venta_id:10), con producto_id 999, que no existe en la tabla productos. Sería un caso de revisión, ya que existe una venta sin un producto asignado, algo que no podría pasar nunca porque es un error — a diferencia de la consulta 1, donde existe un producto que nunca se vendió, algo que sí podría pasar.

## FULL OUTER JOIN en un caso real
**¿Cuándo usarías FULL OUTER JOIN en un caso real de negocio?**

En un caso real usaría el comando FULL OUTER JOIN en un negocio cuando necesite todos los datos de cada tabla más su relación, y los necesite todos sí o sí para hacer un análisis de cierto tipo. Por ejemplo, un negocio el cual tiene una tabla de empleados y otra tabla de capacitaciones realizadas: nos convendría en un caso así traer todos los datos para analizar a todos los empleados que tenemos junto a todas las capacitaciones realizadas, juntando a todos los empleados que hayan hecho 1 o más capacitaciones, y trayendo también los datos de los empleados que nunca realizaron una capacitación.
