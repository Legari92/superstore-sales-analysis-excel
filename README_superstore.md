# Análisis de Ventas y Rentabilidad Superstore

El objetivo de este proyecto es aplicar técnicas de análisis de datos en un entorno realista utilizando Excel, con el fin de extraer conclusiones clave a partir de una base de datos de ventas. A través de la limpieza, transformación y visualización de los datos, se identifican patrones de comportamiento comercial, rentabilidad por segmento y rendimiento de productos, con una presentación final en formato dashboard interactivo.

## Instalación y requisitos

- Excel o cualquier otro visor `.xls`

## Recursos utilizados

- [Link a la tabla original](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final?resource=download)

## EDA

### Transformación y limpieza

1. Limpiamos columnas no necesarias o demasiado granulares (`order #` y `zip code`).
2. Agregamos la columna **Order Month** para trabajar más cómodamente.
3. Cambiamos el formato de fechas a inglés, ya que daba error al intentar pasar los datos a la columna **Order Month**.
4. Damos formato al resto de columnas (moneda, cantidades, etc.).
5. Creamos una nueva columna para porcentajes, ya que el formato actual no lo convierte adecuadamente.
6. La relación entre `sales` y `quantity` no tiene mucho sentido: no puede ser que, por ejemplo, en la primera fila, 2 ventas de 26.196 den 419.136 de beneficio. No deberíamos tener más beneficio que el propio importe de la venta.
7. Quitamos las filas que dan datos irreales, como por ejemplo un beneficio 16 veces superior al precio de la propia venta. Tenemos datos sintéticos, pero intentamos conservar algo de realismo para que no salgan resultados disparatados, y no es que podamos pedirle a nadie contraste o aclaración sobre los datos.

   Para conseguir esto, creamos una nueva columna con una fórmula para verificar si `sales * quantity > profit` devuelve **verdadero**. Después filtramos por verdadero y eliminamos dichas filas.

8. Añadimos un **sales total** (`sales * quantity`) para facilitar el trabajo en las tablas dinámicas.
9. Creamos una columna con **profit %** y comprobamos que en algunas ventas perdemos más del 100%. En la mayoría de casos no debería ser posible o viable para la mayoría de empresas, pero lo dejamos y lo achacamos a que sean datos sintéticos. Podríamos añadir un filtro para eliminar ventas con un `% de profit` menor de `-100%`, pero tampoco quería enrevesarlo.

### Análisis descriptivo

1. Creamos las distintas tablas dinámicas y sus correspondientes gráficos.
2. Evitamos introducir demasiadas tablas y nos apoyamos en la segmentación del dashboard para lograr una visión más completa.

## Dashboard

1. Creo que hay algún conflicto en las fechas porque, después de cambiar el formato varias veces y probar con distintas fórmulas, no he conseguido ponerlo por año.
2. Introducimos las tablas dinámicas.
3. Añadimos segmentadores temporales, de región, envíos y tipos de cliente.

## Resultados y conclusiones

1. **Muebles** es la peor categoría con diferencia, mostrando un ratio de beneficios minúsculo comparado con el resto de categorías.
2. El segmento **Consumer** y **Corporate** tienen un margen de beneficios porcentual inferior al de **Home Office**, aunque tienen mayor volumen de ventas y beneficio total.
3. El envío en **mismo día** tiende a tener unos márgenes de beneficios desproporcionadamente mayores en los tipos de cliente **Consumer** y **Home Office**, pero da pérdidas en **Corporate**. Dichas pérdidas están mayormente ligadas con un solo producto.

   Otros tipos de envíos también sugieren diferencias notables, aunque necesitaría un examen más exhaustivo.

4. El **top 10 de productos por beneficio** representa un porcentaje desproporcionado del total de ganancia, lo cual sugiere una concentración de rentabilidad en pocos ítems.
5. La región **Central** tiene márgenes más bajos en general. Las subcategorías de **Office Supplies** que venden tienen poco margen y la de **Muebles** es una categoría poco rentable en general, traduciéndose en un rendimiento peor que el resto de zonas.

## Autor

- Qiongxi Liu
- [GitHub](https://github.com/Legari92/)
