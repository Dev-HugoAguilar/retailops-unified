# Reproducción del modelo

## Qué contiene el repositorio

`app/index.html` es el artefacto final: incluye la simulación, las cinco variables
del modelo, la media y la escala del escalado, los pesos de la red y las métricas
de los dos modelos comparados.

## Qué no contiene

El pipeline Python que produjo ese artefacto. No hay en este repositorio ni en el
árbol local del autor:

- el generador de la operación sintética con semilla 42;
- el cálculo del objetivo y de las cinco variables;
- la partición de entrenamiento, validación y prueba;
- el entrenamiento de la logística y de la MLP `24/12`;
- la selección del umbral y la evaluación final;
- el exportador del artefacto;
- la comprobación de paridad entre Python y JavaScript.

## Qué se puede verificar hoy

| Comprobación | Estado |
|---|---|
| El artefacto abre y responde en el navegador | sí, verificación automatizada (51 + 8 comprobaciones) |
| Los datos, pesos y métricas están embebidos y son coherentes | sí, el bloque `MODEL` es legible |
| La inferencia se ejecuta sin backend | sí |
| El modelo se puede reentrenar desde el repositorio | **no** |
| Las métricas publicadas se pueden reproducir | **no** |

## Qué haría falta

Recuperar el pipeline original (no escribirlo de nuevo) o publicarlo junto con el
generador con semilla fija, la partición declarada y el exportador, y añadir una
prueba de paridad que compare la probabilidad calculada en Python con la que
calcula el JavaScript sobre el mismo registro.

## Por qué no se reconstruyó

Una reconstrucción nueva produciría otros pesos y otras métricas, y atribuir al
generador nuevo los resultados antiguos sería una afirmación falsa. El repositorio
declara la limitación en lugar de taparla.
