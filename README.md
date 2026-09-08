# Modelo de datos y medidas DAX - TechStore

Este proyecto contiene el modelo analítico de TechStore desarrollado en Power BI a partir del pipeline ETL realizado previamente con Power Query y lenguaje M.

## Objetivo

Construir un modelo de datos en esquema estrella, establecer relaciones activas entre las tablas y crear una tabla centralizada de medidas utilizando DAX para el análisis de ventas.

## Modelo de datos

El modelo está compuesto por las siguientes tablas:

- `Dim_Clientes`
- `Dim_Productos`
- `Dim_Categorias`
- `Dim_Fechas`
- `Fact_Ventas`

Las relaciones establecidas son:

- `Dim_Clientes[id_cliente]` → `Fact_Ventas[id_cliente]`
- `Dim_Productos[id_producto]` → `Fact_Ventas[id_producto]`
- `Dim_Categorias[id_categoria]` → `Dim_Productos[id_categoria]`
- `Dim_Fechas[Date]` → `Fact_Ventas[fecha_venta]`

Las relaciones utilizan cardinalidad 1:N, dirección de filtro única y se encuentran activas.

## Tabla de fechas

Se creó `Dim_Fechas` utilizando el rango de fechas disponible en `Fact_Ventas`.

La tabla incluye las siguientes columnas calculadas:

- `Date`
- `Año`
- `Mes Número`
- `Mes Nombre`
- `Trimestre`
- `Semana`

La columna `Date` se utiliza como columna de fecha principal para las relaciones y los cálculos de inteligencia temporal.

## Medidas DAX

Se creó una tabla dedicada `Medidas` para centralizar las medidas principales del modelo.

Las medidas desarrolladas son:

- `Total Ventas`
- `Ventas Online`
- `Ventas YTD`
- `Ventas LY`
- `% Crecimiento Anual`

Estas medidas permiten analizar las ventas totales, las ventas realizadas por canal online, la acumulación anual, la comparación con el año anterior y el crecimiento porcentual interanual.

## Validación

Se creó la página `Validación` con una matriz que permite comprobar el funcionamiento de las medidas por:

- Mes
- Año
- Total Ventas
- Ventas YTD
- Ventas LY
- % Crecimiento Anual

La validación permite comprobar la acumulación de ventas durante el año y la comparación de los períodos con el año anterior.

## Resultado

El archivo `.pbix` contiene el modelo de datos relacionado, la tabla de fechas, las medidas DAX y la página de validación necesarias para continuar con el análisis y la visualización de los datos de TechStore.
