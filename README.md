RetailChain — UNION y UNION ALL

-- ¿Cuántas filas devuelve cada consulta y por qué son distintas? --

  La consulta realizada con UNION devuelve 11 filas, mientras que la consulta realizada con UNION ALL devuelve 14 filas. La diferencia se   debe a que UNION elimina las filas completamente duplicadas entre los resultados de ambas consultas.
  En este ejercicio existen tres productos que tienen el mismo id_producto, nombre_producto y categoria en ambas sucursales:
  103 — Monitor 4K 27"
  104 — Teclado Mecánico
  106 — SSD Externo 1TB
  Como estas filas son idénticas en las columnas seleccionadas para construir el catálogo, UNION mantiene solamente una instancia de cada   una.
  Por este motivo, de los 14 registros originales se eliminan 3 duplicados y el catálogo resultante contiene 11 filas.
  La Webcam HD 1080p aparece dos veces porque tiene distintos identificadores: 107 en la Sucursal Norte y 111 en la Sucursal Sur. Aunque    el nombre y la categoría sean iguales, la fila completa no es idéntica y por eso UNION conserva ambos registros.

-- ¿Por qué UNION ALL es más eficiente que UNION? --

  UNION ALL suele ser más eficiente porque simplemente combina los resultados de ambas consultas y conserva todas las filas. UNION, en      cambio, debe realizar una operación adicional para identificar y eliminar registros duplicados. Para hacerlo, el motor de base de datos   debe comparar los resultados, normalmente mediante operaciones internas de ordenamiento. Estas operaciones adicionales consumen           memoria, procesamiento y tiempo, especialmente cuando se trabaja con grandes volúmenes de datos.
  Por esta razón, cuando no es necesario eliminar duplicados, utilizar UNION ALL suele ser una mejor opción.

-- ¿En qué casos de negocio usaría cada uno? --

  Utilizaría UNION cuando el objetivo sea obtener un conjunto de valores únicos provenientes de diferentes fuentes. Por ejemplo, podría     utilizarse para combinar listas de clientes provenientes de dos sistemas y crear una lista unificada sin registros repetidos. Otro caso   podría ser consolidar una lista de proveedores provenientes de distintas unidades de negocio para obtener un catálogo general de          proveedores únicos.

  Utilizaría UNION ALL cuando cada registro tenga valor por sí mismo y sea necesario conservar toda la información. Por ejemplo, podría     utilizarse para consolidar las transacciones de ventas de diferentes sucursales. Aunque un mismo producto aparezca muchas veces, cada     transacción representa una operación diferente y no debería eliminarse. Otro ejemplo sería consolidar registros de producción de          diferentes plantas para calcular el volumen total producido por una compañía.

-- ¿Qué pasa si las columnas de ambas consultas no coinciden en número o tipo? --

  Para utilizar UNION o UNION ALL, ambas consultas deben devolver el mismo número de columnas y estas deben aparecer en el mismo orden.     Además, los tipos de datos correspondientes deben ser iguales o compatibles entre sí. SQL arrojará un error cuando las tablas que se      quieren unir tienen diferente cantidad de columnas, por ejemplo si la tabla1 tiene cuatro columnas y la tabla2 solamente tres columnas.
  También pueden generarse errores o conversiones de datos no deseadas si las columnas correspondientes utilizan tipos de datos             incompatibles, por ejemplo si la tabla1 tiene una columna de productos identidicados por numeros y la tabla2 estan identificados en       formato texto. 
