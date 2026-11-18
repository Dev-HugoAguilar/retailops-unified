# RetailOps Unified

*Machine learning para operación de supermercados*

Prototipo de inteligencia operativa que conecta ventas por sucursal, disponibilidad de productos, preparación de pedidos, capacidad de personal, reparto y experiencia del cliente. Compara una red neuronal y una regresión logística para anticipar retrasos, permite inspeccionar sus probabilidades y probar una inferencia con los pesos entrenados dentro del navegador. La demo combina ubicaciones recopiladas de tiendas de CDMX con una operación completamente simulada y reproducible. No es un producto oficial de Walmart ni utiliza sus ventas, inventario o datos internos.

**Prototipo funcional · Machine Learning**

## Problema

Una operación de supermercado puede vender más de lo que logra preparar y entregar dentro de la promesa. Analizar ventas, inventario, personal y satisfacción en pantallas aisladas dificulta distinguir dónde se concentra un problema, qué pedidos están expuestos y qué capacidad existe para atenderlos. Además, una probabilidad de retraso pierde valor si se presenta sin referencia, sin explicar cuándo se calcula o como si una reasignación demostrara una mejora causal.

## Destinatario

Equipos de operaciones de retail, comercio electrónico, preparación y última milla, junto con responsables de analítica y machine learning que buscan explorar cómo conectar indicadores comerciales con decisiones operativas y predicciones inspeccionables antes de un piloto con datos reales.

## Mi contribución

Diseñé e implementé un prototipo con siete vistas conectadas: negocio, pedidos y picking, inventario, personal, experiencia, machine learning y evidencia. Construí un mapa de calor de ventas simuladas por sucursal, con límites de alcaldías, ranking y selección vinculada; una matriz temporal de demanda; paneles horarios de demanda y capacidad; visualizaciones de productos, calibración y riesgo; y una traza de las transiciones realizadas durante la sesión. Modelé la asignación por sucursal, rol, turno y plazas disponibles, el cierre de picking con validación atómica y descuento único de stock, las sustituciones manuales y el registro de entrega con evaluación opcional. Entrené y comparé una regresión logística y una MLP, exporté sus parámetros y conecté la red neuronal a un laboratorio de inferencia local. Separé las reglas del dominio de la presentación y preparé las comprobaciones y el paquete reproducible para integrar la demo en el portafolio.

## Fuentes y datos

El catálogo contiene 51 ubicaciones de Walmart Supercenter y Express recopiladas de un directorio secundario de BizLocationDB, con cotejo oficial limitado; es una lista parcial y no garantiza vigencia ni exhaustividad. El mapa incorpora las geometrías de referencia de las 16 alcaldías seleccionadas del proyecto sociohidrológico SHI CDMX de 2021. Las 51 coordenadas tienen una coincidencia espacial única en esa capa y el directorio contiene tiendas en 13 de las 16 alcaldías; eso no representa cobertura comercial completa de la ciudad. La operación se genera con semilla 42: 12,000 pedidos sobre 120 días sintéticos, 18 productos, 153 personas y 918 registros de inventario por sucursal y SKU. Los últimos 150 pedidos forman la fotografía operativa. Pedidos, precios de ejemplo, turnos, existencias, evaluaciones y resultados son simulados; no son datos de Walmart ni información en tiempo real.

## Método y decisiones técnicas

Definí como objetivo de clasificación si la duración total del simulador supera la promesa de entrega. Las cinco entradas son número de referencias distintas, carga inicial sintética, distancia, promesa y hora de creación; el número de referencias no se confunde con la suma de unidades. Comparé una referencia constante de prevalencia, regresión logística y una MLP de arquitectura 5 → 24 → 12 → 1. La separación por bloques de días sintéticos reserva 8,400 ejemplos para entrenamiento, 1,800 para validación y 1,800 para prueba. El escalado se ajusta solo con entrenamiento; la MLP de esta versión no utiliza un split aleatorio interno de early stopping. Los umbrales se eligen únicamente en validación con costos hipotéticos de 5 para un retraso no detectado y 1 para una falsa alerta. La evaluación incluye ROC-AUC, precisión promedio —AP—, Brier, matriz de confusión y curva de fiabilidad. Los pesos y el escalado exportados ejecutan la inferencia en JavaScript, sin un servidor de modelos.

El mapa suaviza el importe de cada sucursal con un núcleo gaussiano de σ aproximada de 2 km y composición por máximo local: las tiendas cercanas no se suman para aparentar una sola sucursal más vendedora. La sucursal líder se obtiene de su importe exacto. Ventas simuladas significa valor de artículos surtidos en pedidos entregados, conservando el precio original; ticket surtido es ese importe dividido por el número de entregas. Los filtros de sucursal, alcaldía, formato y periodo coordinan las vistas; inventario y personal mantienen su naturaleza de fotografía actual. Los resultados futuros de pedidos activos se ocultan y cambiar una asignación no modifica artificialmente la probabilidad original.

## Resultados publicados

La demo disponible permite recorrer una sucursal desde su desempeño comercial hasta un pedido, su preparación, disponibilidad, asignación, entrega y bitácora. Incluye el calor de ventas, la identificación de la tienda líder, zoom con porcentaje, retorno a la extensión de CDMX y el laboratorio de inferencia MLP. En el bloque sintético de prueba, la MLP obtiene ROC-AUC de 0.9859, AP de 0.9540 y Brier de 0.04017, frente a 0.9856, 0.9527 y 0.04020 de la regresión logística. La referencia constante obtiene ROC-AUC de 0.5000, AP de 0.2233 y Brier de 0.17351. El umbral seleccionado es 0.12 para la MLP y 0.14 para la logística. Son resultados del simulador, no resultados de una operación real. La implementación JavaScript de la MLP coincide con scikit-learn en los 150 ejemplos operativos con diferencia absoluta menor a 1e-12. La versión empaquetada registra 32 comprobaciones aprobadas: 12 de dominio, 6 del campo de calor y 14 de estructura e interacción DOM.

## Limitaciones

Es un prototipo reproducible, no una plataforma de retail en producción. La calidad predictiva refleja el generador sintético; no demuestra generalización, ahorro o reducción de retrasos en Walmart u otra empresa. La diferencia entre MLP y logística es pequeña y no se ha establecido superioridad estadística; faltan intervalos, evaluación externa y validación de utilidad comercial. No hay un pronóstico de demanda entrenado, optimización de rutas ni evidencia causal de que reasignar personas reduzca el riesgo. La carga de entrada es sintética y no se recalcula desde las asignaciones. El inventario inicial es una fotografía y no una reconciliación de las 12,000 compras históricas; las sustituciones no validan alérgenos o equivalencia nutricional. No se modelan cobros, costos, devoluciones, impuestos desglosados ni margen. Las calificaciones corresponden a pedidos y no se atribuyen causalmente al trabajador. El estado y la bitácora viven en memoria y se pierden al recargar. La lista de tiendas es parcial y los límites cartográficos son de referencia. Las pruebas DOM no equivalen a comprobar clics físicos, foco y layout en un navegador; esa revisión en la integración del portafolio sigue pendiente. La publicación del portafolio debe verificarse antes de marcar el proyecto como publicado.

## Tecnologías

### Datos y machine learning

Python · NumPy · scikit-learn · StandardScaler · LogisticRegression · MLPClassifier · validación por bloques temporales sintéticos

### Interfaz y cartografía

JavaScript · HTML/CSS · SVG · GeoJSON · mapa de calor ponderado · inferencia MLP en navegador

### Verificación y entrega

Node.js · LinkeDOM · pruebas de dominio, intensidad y DOM · verificación SHA-256 · paquete autónomo de integración

## Referencias de procedencia

- Directorio de tiendas: https://bizlocationdb.com/locations/walmart/mexico/r/mexico-city
- Geometrías de referencia: https://github.com/npalomin/shi_dataset_cdmx/blob/main/alcaldias.geojson
- Inspiración de visualización: https://www.dataviz-inspiration.com/

## Nota para el integrador

Categoría principal obligatoria: **Machine Learning**. Usa el identificador real de esa categoría en el portafolio, sin crear una variante duplicada. El estado editorial actual es **Prototipo funcional**; si ese estado no existe en el esquema, utiliza el estado no publicado equivalente y conserva la descripción. Cambia a Publicado solo cuando la ruta de la ficha y la demo hayan sido publicadas y comprobadas. Esta nota orienta la implementación; no es un bloque visible de la ficha pública.
