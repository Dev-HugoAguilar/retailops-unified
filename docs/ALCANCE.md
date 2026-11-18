# Procedencia, atribuciones y alcance

## Qué es real y qué es simulado

| Elemento | Naturaleza |
|---|---|
| Catálogo de 51 sucursales | Recopilado de un directorio secundario (BizLocationDB), con cotejo oficial limitado. |
| Geometrías de alcaldías | Datos públicos de referencia de un repositorio abierto. |
| Ventas, surtido, pedidos, personal, calificaciones | **Generados** por un modelo determinista para la demostración. |
| Pesos del modelo de clasificación | Entrenados sobre el generador sintético; embebidos en la página. |
| Resultados y métricas del modelo | Describen el generador, no el desempeño de una operación real. |

Ninguna cifra de esta aplicación proviene de sistemas internos de una cadena
comercial. El proyecto no tuvo acceso a información confidencial.

## Atribuciones

- **Directorio de tiendas**:
  <https://bizlocationdb.com/locations/walmart/mexico/r/mexico-city>
- **Geometrías de alcaldías (referencia)**:
  <https://github.com/npalomin/shi_dataset_cdmx/blob/main/alcaldias.geojson>
- **Inspiración de visualización**: <https://www.dataviz-inspiration.com/> y sus
  variantes de mapa de calor y de línea, citadas en la aplicación.

Las fuentes citadas conservan sus condiciones de uso. Este repositorio no
relicencia esos materiales ni incluye un archivo `LICENSE` propio.

## Definiciones que la interfaz respeta

- **Ventas**: valor de los artículos surtidos en la simulación. No equivale a
  cobros, ingresos, margen ni demanda.
- **Cobertura geográfica**: 51 ubicaciones, 13 de 16 alcaldías con al menos una
  tienda. La lista es parcial y no representa la red completa.
- **Calor**: importe suavizado por un núcleo gaussiano de σ ≈ 2 km con composición
  por máximo local. No es una suma de ventas por zona.
- **Promesa de entrega**: umbral del simulador. Superarlo define la clase positiva
  del modelo.
- **Duración total**: suma de preparación, asignación y reparto simulados.

## Límites de interpretación

- El prototipo es reproducible, no una plataforma de retail en producción.
- La red neuronal se evalúa con bloques temporales sintéticos; una mejora frente a
  la regresión logística en ese contexto no implica ventaja fuera de él.
- El mapa sirve para comparar sucursales dentro de la simulación; no para decidir
  ubicaciones, inventarios ni personal.
- No se midió rendimiento en dispositivos de gama baja ni en navegadores distintos
  de los usados en la verificación.

## Integridad del archivo

`app/index.html` se publica como archivo regular de 13,416,449 bytes con SHA-256
`CDC6D7C930ECEA96F9A61CCFBCDC18FA3BC96B9968E084D5B24A4DBE01D00AB5`. Se decidió no
usar Git LFS: el tamaño está muy por debajo del límite de GitHub y el valor del
repositorio es poder abrir el prototipo sin instalar herramientas adicionales.
