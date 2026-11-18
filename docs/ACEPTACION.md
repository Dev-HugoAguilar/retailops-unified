# Lista de aceptación / RetailOps

## Entrada desde el portafolio

- [ ] Está registrado con el ID real de la categoría principal Machine Learning y aparece al aplicar ese filtro.
- [ ] Hay una sola tarjeta de RetailOps; no se creó otra categoría similar ni una tarjeta duplicada.
- [ ] La tarjeta abre la ficha nativa del portafolio antes de la demo.
- [ ] La ficha conserva título, subtítulo, resumen, estado y categoría según la plantilla existente.
- [ ] Se leen completos los ocho apartados: Problema, Destinatario, Mi contribución, Fuentes y datos, Método y decisiones técnicas, Resultados publicados, Limitaciones y Tecnologías.
- [ ] Los apartados se cargan desde el contenido entregado; no son placeholders ni un README sin mostrar.
- [ ] Tecnologías conserva sus agrupaciones y no atribuye librerías o servicios inexistentes.
- [ ] El CTA Ver demo abre RetailOps funcional y permite regresar a Machine Learning.
- [ ] No se marca Publicado sin comprobar la publicación y sus URLs.
- [ ] El enlace funciona con la base de publicación del proyecto, incluyendo subdirectorios si existen.
- [ ] Otros proyectos mantienen sus rutas y estilos.
- [ ] Se conserva la indicación de operación simulada.

## Mapa de calor

- [ ] Primera vista: Calor por sucursal / Ventas simuladas.
- [ ] Hay una capa de intensidad continua: no se muestran solo puntos ni solo alcaldías coloreadas.
- [ ] Se ven las 51 tiendas y los límites de las 16 alcaldías de referencia.
- [ ] Nombre e importe de la tienda líder coinciden con el cálculo exacto y el ranking.
- [ ] Los cambios de formato y periodo recalculan calor, ranking y líder.
- [ ] No se suman vecinas para producir una falsa sucursal líder.
- [ ] Se conserva la explicación de radio visual, procedencia y cobertura parcial.

## Controles / navegador real

- [ ] Desde 100 %, un clic en + lleva a 130 %, sin doble ejecución.
- [ ] Un clic en − vuelve a 100 % y el botón se desactiva en el mínimo.
- [ ] ↺ restaura extensión completa y elimina el desplazamiento acumulado.
- [ ] Ubicar líder centra esa tienda a 300 %, manteniendo filtros.
- [ ] Se puede arrastrar; el arrastre no dispara un filtro de tienda.
- [ ] Los botones siguen recibiendo clics después de arrastrar.
- [ ] Cambiar entre Calor, Sucursales y Alcaldías actualiza la vista y el estado activo.
- [ ] Cambiar Ventas, Pedidos y Retrasos actualiza la capa y la leyenda.
- [ ] Clic en tienda/ranking o alcaldía conecta los filtros del resto del tablero.

## Operación

- [ ] Se recorre pedido → asignación → picking → stock → reparto → entrega → bitácora.
- [ ] No se permite stock negativo ni doble descuento.
- [ ] Asignación respeta rol, sucursal, turno y plazas.
- [ ] Reiniciar reproduce el estado normalizado original.
- [ ] La evaluación ausente no se contabiliza como cero.
- [ ] ML distingue resultados simulados e inferencia; no modifica la probabilidad por un clic de asignación.

## Presentación y validación

- [ ] 1440, 1024 y 390 px: sin desbordamiento horizontal global; tablas/kanban pueden usar su scroll interno.
- [ ] Navegación, diálogo y controles utilizables con teclado y foco visible.
- [ ] Movimiento reducido respetado.
- [ ] Sin errores JavaScript en la ruta integrada.
- [ ] Se ejecutaron las pruebas del código modificado y la compilación propia del portafolio.
- [ ] La evidencia visual identifica URL y entorno; no se confunde con una captura generada a partir del SVG.
