# Historial de cambios

El formato sigue [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/) y
las versiones usan [Versionado Semántico](https://semver.org/lang/es/).

## [1.0.0] — 2026-11-26

### Añadido

- Primera publicación como repositorio independiente.
- Aplicación autocontenida con siete vistas conectadas: negocio, pedidos y
  *picking*, inventario, personal, experiencia, machine learning y evidencias.
- Modelo de clasificación declarado de extremo a extremo: objetivo, cinco
  entradas, `StandardScaler`, `MLPClassifier` frente a `LogisticRegression` y
  validación por bloques temporales sintéticos.
- Inferencia de la red en el navegador con los pesos embebidos, sin backend.
- Mapa de calor con núcleo gaussiano de σ ≈ 2 km y composición por máximo local.
- Recorrido completo de un pedido: por asignar, en preparación, listo, en reparto
  y entregado, con eventos y calificación.
- Ficha editorial, criterios de aceptación y documentación de procedencia y
  límites.
- Integración continua de integridad y de verificación de credenciales.

### Nota

El proyecto se extrae del portafolio de datos de Hugo Aguilar. El archivo de
aplicación se versiona como archivo regular, sin Git LFS.
