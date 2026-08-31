# Pipeline ETL - TechStore

Este proyecto contiene un pipeline ETL desarrollado en Power BI utilizando Power Query y lenguaje M.

## Objetivo

Limpiar, transformar y preparar los datos de TechStore para utilizarlos posteriormente en un modelo analítico en Power BI.

## Transformaciones realizadas

* Eliminación de registros duplicados utilizando las columnas de ID como clave.
* Corrección de tipos de datos.
* Renombrado de consultas con nomenclatura dimensional:

  * `Dim_Clientes`
  * `Dim_Productos`
  * `Dim_Categorias`
  * `Fact_Ventas`
* Merge entre `Fact_Ventas` y `Dim_Productos` para incorporar `nombre_producto` y `categoria`.
* Documentación de transformaciones mediante comentarios técnicos en lenguaje M.

## Tratamiento de nulos y duplicados

En `Dim_Clientes` se eliminaron duplicados por `id_cliente`. Los valores nulos de `email` y `ciudad` se reemplazaron por `"Sin datos"` para conservar los registros de clientes y evitar pérdida innecesaria de información.

En `Dim_Productos` se eliminaron duplicados por `id_producto`. Los registros con `precio` nulo se eliminaron porque el precio es necesario para calcular correctamente los ingresos. También se eliminaron los productos sin categoría para evitar clasificaciones incompletas en los análisis.

## Resultado

El archivo `.pbix` contiene las tablas limpias y estructuradas para continuar con el modelado de datos y la creación de medidas y visualizaciones en Power BI.
