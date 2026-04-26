# REFLEXION

## Opción elegida
Opción A — Múltiples tags en un solo pipeline.

## Qué hice
Actualicé el contenido de `index.html`, hice commit de los cambios y publiqué una nueva versión usando el tag `v1.1.0`. Luego verifiqué en GitHub Container Registry que la imagen quedó publicada con la nueva versión y que la etiqueta `latest` apuntó a la más reciente.

## 1. ¿Qué ventaja tiene disparar el pipeline con un tag en lugar de con cada push? ¿Cómo cambia el flujo de trabajo del equipo?

Disparar el pipeline con un tag permite separar claramente el trabajo de desarrollo del proceso de publicación. Durante el desarrollo, el equipo puede hacer múltiples commits y pushes sin generar una nueva imagen lista para distribución en cada cambio. En cambio, el tag representa una decisión explícita de release. Esto mejora el control, evita publicaciones accidentales y hace que el flujo de trabajo sea más ordenado. El equipo puede desarrollar de forma continua, pero solo publicar versiones cuando realmente están validadas.

## 2. ¿Cuál es la diferencia entre usar `latest` y una versión específica como `1.0.0` al desplegar en producción?

La etiqueta `latest` siempre apunta a la imagen más reciente publicada, pero no garantiza estabilidad ni reproducibilidad. Si se usa en producción, una actualización futura puede cambiar el comportamiento del sistema sin que el equipo controle exactamente qué versión se está ejecutando. En cambio, usar una versión específica como `1.0.0` asegura que el despliegue sea predecible, repetible y fácil de auditar. En producción es más seguro usar versiones fijas y dejar `latest` para pruebas rápidas o entornos menos críticos.

## 3. El proyecto anterior ya tenía 6 tags creados. ¿Qué significaría haber tenido este workflow desde el principio?

Haber tenido este workflow desde el principio habría significado que cada tag importante del proyecto habría generado automáticamente una imagen Docker versionada en GHCR. Eso permitiría reconstruir la historia de releases del proyecto, recuperar versiones anteriores fácilmente y mantener trazabilidad entre código, imagen y despliegue. En otras palabras, el proyecto tendría una cadena DevOps más madura, con releases reproducibles desde el inicio.

## Conclusión

Esta práctica demuestra que los tags no solo sirven para marcar versiones en Git, sino también para controlar cuándo se publica una imagen Docker. El uso de GHCR junto con GitHub Actions permite automatizar releases de forma profesional y mantener un historial claro de versiones.
