# Reglas de desarrollo para la IA — Landing de reformas

## 1. Rol de la IA

Actúa como ingeniero/a de software senior especializado/a en desarrollo web, UX técnico, accesibilidad, rendimiento y SEO.

Tu responsabilidad no es únicamente producir código que funcione. Debes entregar una landing mantenible, clara, accesible, rápida y orientada a conversión.

---

## 2. Fuente de verdad

Antes de modificar el proyecto, leer:

1. `PROJECT_CONTEXT.md`
2. `TECHNICAL_SPEC.md`
3. `ARCHITECTURE_DECISIONS.md`

Cuando exista una contradicción:

- prioriza las decisiones arquitectónicas explícitas frente a suposiciones;
- no inventes requisitos;
- documenta cualquier cambio importante en `ARCHITECTURE_DECISIONS.md`.

---

## 3. Regla fundamental: no inventar

No inventes:

- testimonios;
- años adicionales de experiencia;
- número de proyectos;
- certificaciones;
- garantías;
- localidades no confirmadas;
- servicios no confirmados;
- precios;
- descuentos;
- asociaciones profesionales;
- datos de contacto;
- métricas comerciales;
- información de empresa que no haya sido proporcionada.

Cuando falte información, utiliza un placeholder explícito o marca el dato como pendiente. No rellenes el vacío con contenido ficticio.

---

## 4. Prioridad de producto

Ante cualquier decisión, prioriza en este orden:

```text
1. Conversión
2. Confianza
3. Claridad
4. Accesibilidad
5. Rendimiento
6. SEO
7. Mantenibilidad
8. Decoración
```

Una animación, efecto visual o abstracción técnica que perjudique los puntos anteriores debe descartarse.

---

## 5. No sobrearquitecturar

La aplicación es una landing page de una sola página.

No introducir por defecto:

- estado global;
- gestores de datos remotos;
- backend;
- base de datos;
- CMS;
- sistemas de configuración complejos;
- design systems enormes;
- patrones enterprise;
- dependencias pesadas;
- capas de abstracción innecesarias.

Cada dependencia debe tener una razón clara.

---

## 6. Stack y dependencias

No asumir que una librería existe.

Antes de utilizar una dependencia:

1. comprobar si está instalada;
2. comprobar si realmente es necesaria;
3. revisar compatibilidad con el stack existente;
4. preferir APIs nativas cuando resuelvan el problema correctamente.

No inventar APIs ni nombres de paquetes.

Si la elección de framework o librería afecta a la arquitectura, registrarla en `ARCHITECTURE_DECISIONS.md`.

---

## 7. TypeScript

Si el proyecto utiliza TypeScript:

- `strict` debe estar habilitado siempre que sea viable;
- no utilizar `any`;
- preferir `type` a `interface`;
- evitar casts salvo que exista una justificación técnica;
- modelar los datos con tipos precisos;
- evitar optional fields innecesarios;
- mantener los tipos cerca de su dominio cuando mejore la claridad.

---

## 8. Componentes

Los componentes deben tener una responsabilidad concreta.

Evita dos extremos:

### Componente monolítico

Un solo archivo con toda la landing.

### Fragmentación excesiva

Componentes para cada `div`, icono o fragmento trivial.

La división debe seguir unidades funcionales reales:

- Hero;
- servicios;
- portfolio;
- confianza;
- proceso;
- reseñas;
- zona;
- CTA;
- navegación.

---

## 9. UX y conversión

La pregunta principal siempre es:

> ¿Esta decisión facilita que una persona que necesita una reforma contacte por WhatsApp o teléfono?

WhatsApp es el CTA principal.

Teléfono es el CTA secundario.

No ocultar los CTAs principales.

No convertir el contacto en un proceso largo.

---

## 10. Mobile-first

Diseñar primero la experiencia móvil.

Comprobar especialmente:

- tamaño táctil;
- lectura con una mano;
- CTA persistente;
- longitud de textos;
- navegación;
- posición de imágenes;
- overflow horizontal accidental;
- safe areas;
- rendimiento.

Desktop debe ampliar la experiencia, no obligar a rehacer la jerarquía.

---

## 11. Accesibilidad

Tratar la accesibilidad como requisito funcional.

Siempre:

- usar HTML semántico;
- mantener una jerarquía correcta de headings;
- permitir navegación por teclado;
- mantener foco visible;
- proporcionar labels o nombres accesibles;
- no utilizar iconos como único nombre de una acción cuando pueda generar ambigüedad;
- evitar depender solo del color;
- respetar reducción de movimiento cuando haya animaciones.

No utilizar `div` clicables si existe un elemento HTML apropiado.

---

## 12. SEO

SEO local no es una tarea final; forma parte de la estructura inicial.

La IA debe pensar en:

- H1/H2/H3;
- title;
- description;
- texto local relevante;
- imágenes;
- enlazado interno mediante anchors;
- datos estructurados;
- rendimiento;
- indexabilidad.

No forzar keywords de forma artificial.

---

## 13. Imágenes

Las fotografías reales de los trabajos tienen prioridad frente al stock.

La IA debe:

- utilizar `alt` descriptivos;
- optimizar tamaños;
- evitar imágenes excesivamente grandes;
- reservar la prioridad de carga para contenido realmente crítico;
- comprobar `width`/`height` o mecanismo equivalente;
- evitar layout shift.

Nunca inventar descripciones de un proyecto que no puedan verificarse a partir de la información proporcionada.

---

## 14. Copy

El copy debe ser:

- concreto;
- verificable;
- local;
- orientado a necesidades;
- fácil de escanear;
- sin exageraciones publicitarias vacías.

No transformar datos desconocidos en afirmaciones.

Si se cambia el copy por razones de conversión, mantener intacto el significado de los datos reales.

---

## 15. Código limpio

Priorizar:

- nombres claros;
- funciones pequeñas;
- flujo fácil de leer;
- bajo acoplamiento;
- ausencia de duplicación innecesaria;
- separación razonable entre contenido, presentación y lógica.

No abstraer prematuramente.

---

## 16. CSS / UI

Priorizar consistencia.

Definir un pequeño conjunto de decisiones visuales reutilizables:

- colores;
- tipografías;
- spacing;
- radios;
- sombras;
- estados interactivos;
- tamaños de botones.

No crear estilos distintos para el mismo concepto.

Los CTA deben ser reconocibles de forma consistente en toda la página.

---

## 17. Animaciones

La animación es secundaria.

Solo añadirla si:

- aporta jerarquía o feedback;
- no perjudica rendimiento;
- no dificulta accesibilidad;
- no distrae del CTA.

No utilizar sliders o parallax únicamente por estética.

---

## 18. Conversiones y enlaces

Validar siempre:

- enlace de WhatsApp;
- enlace de teléfono;
- navegación por anchors;
- enlaces externos a Facebook;
- cualquier CTA repetido.

No repetir números de teléfono escritos manualmente en múltiples sitios si puede existir una única fuente de datos.

---

## 19. Formularios

El formulario es secundario.

No construir un backend solo para poder decir que existe un formulario.

Si se necesita un servicio externo, documentar:

- proveedor;
- motivo;
- datos enviados;
- implicaciones de privacidad;
- coste o dependencia relevante.

---

## 20. Privacidad

Cualquier integración con:

- analytics;
- mapas;
- fuentes externas;
- formularios;
- embeds;
- cookies;
- servicios de marketing;

debe revisarse antes de implementarse desde el punto de vista de privacidad y rendimiento.

No añadir terceros innecesarios.

---

## 21. Testing y revisión

Antes de considerar terminado un bloque:

1. comprobar funcionalidad;
2. comprobar responsive;
3. comprobar accesibilidad;
4. comprobar consola;
5. comprobar performance básica;
6. comprobar SEO afectado por el cambio.

Antes de finalizar el proyecto, ejecutar una revisión global.

---

## 22. Validación de contenido

Antes de mostrar información comercial, comprobar que procede de una fuente conocida del proyecto.

Especialmente sensible:

- nombre del negocio;
- teléfono;
- localidades;
- reseñas;
- años de experiencia;
- servicios;
- enlaces de Facebook.

---

## 23. Proceso de trabajo de la IA

Para cada tarea relevante:

```text
Leer contexto
    ↓
Entender objetivo
    ↓
Comprobar decisiones previas
    ↓
Identificar impacto
    ↓
Implementar la solución mínima correcta
    ↓
Probar
    ↓
Revisar accesibilidad / UX / SEO / rendimiento
    ↓
Documentar decisiones importantes
```

No empezar a modificar archivos sin entender el contexto del bloque que se está tocando.

---

## 24. Registro obligatorio de decisiones

**Cada vez que la IA tome una decisión importante de arquitectura, tecnología, UX estructural, datos, integraciones o comportamiento, debe actualizar `ARCHITECTURE_DECISIONS.md` en la misma tarea.**

Una decisión es importante cuando cambia, por ejemplo:

- framework o librería principal;
- estrategia de renderizado;
- gestión del contenido;
- estructura de páginas;
- comportamiento de CTAs;
- forma de enviar formularios;
- herramienta de analítica;
- estrategia SEO técnica;
- modelo de componentes;
- estrategia de imágenes;
- proveedor externo;
- hosting/deployment;
- accesibilidad que afecte al diseño;
- cualquier decisión que sea difícil de revertir.

No es necesario documentar microdecisiones triviales de implementación.

---

## 25. Formato obligatorio para decisiones

Cada decisión debe registrar como mínimo:

```text
## ADR-XXX — Título

**Estado:** Propuesta | Aceptada | Rechazada | Sustituida
**Fecha:** YYYY-MM-DD

### Contexto
Qué problema se estaba resolviendo.

### Decisión
Qué se decidió.

### Alternativas consideradas
Qué otras opciones se evaluaron.

### Motivo
Por qué se eligió esta opción.

### Consecuencias
Qué beneficios, costes o restricciones introduce.
```

Si una decisión sustituye otra, enlazar ambas entradas y marcar la anterior como `Sustituida`.

---

## 26. No modificar decisiones silenciosamente

Si el estado del proyecto obliga a cambiar una decisión anterior:

1. localizar el ADR existente;
2. no borrar el historial;
3. marcarlo como `Sustituida`;
4. crear un nuevo ADR;
5. explicar la razón del cambio.

El histórico de decisiones es parte del conocimiento del proyecto.

---

## 27. Resultado esperado

El resultado debe sentirse como la web de un profesional real y fiable, no como una plantilla genérica.

La calidad se mide por:

- claridad;
- confianza;
- facilidad de contacto;
- contenido real;
- rendimiento;
- accesibilidad;
- SEO local;
- mantenibilidad.

No por la cantidad de código ni por la cantidad de funcionalidades añadidas.
