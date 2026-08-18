# Decisiones arquitectónicas y funcionales

Este documento es el registro histórico de las decisiones relevantes del proyecto.

La IA de desarrollo **debe actualizar este fichero cada vez que tome una decisión importante** relacionada con arquitectura, tecnología, UX estructural, contenido, integraciones, SEO técnico, rendimiento, accesibilidad o comportamiento.

No borrar decisiones anteriores. Cuando una decisión cambie, marcar la anterior como `Sustituida` y crear un nuevo ADR.

---

## Estado inicial del proyecto

El proyecto es una landing page de una sola página para un profesional particular de reformas.

### Objetivo principal

Conseguir:

1. conversaciones por WhatsApp;
2. llamadas telefónicas.

WhatsApp tiene prioridad como CTA principal.

### Público

- Propietarios de vivienda.
- Personas que acaban de comprar una vivienda.
- Personas que quieren reformar baño/cocina.
- Negocios/locales.
- Personas que necesitan trabajos concretos como pintura, fontanería o pladur.

### Datos confirmados

- 10 años de experiencia.
- Compra de materiales por parte del profesional.
- Zona principal: Alhama de Murcia.
- Según el trabajo, desplazamiento hacia Murcia y Lorca aproximadamente hasta media hora en coche.
- Fotografías reales disponibles.
- Reseñas reales en Facebook.
- Presupuestos sin compromiso.
- Teléfono / WhatsApp: `+34 643 93 26 83`.

---

# ADRs

## ADR-001 — Landing de una sola página

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

El objetivo principal es conseguir contactos, no crear una web corporativa compleja.

### Decisión

Construir inicialmente una única landing page con navegación interna mediante anchors.

### Alternativas consideradas

- Web multipágina.
- Blog independiente.
- Página individual por servicio.

### Motivo

Una única landing reduce fricción, concentra la propuesta de valor y permite orientar toda la experiencia hacia WhatsApp y teléfono.

### Consecuencias

- Menor complejidad.
- Menor coste de mantenimiento.
- SEO más concentrado en una única URL.
- Si posteriormente se detecta una oportunidad SEO suficiente, podrán añadirse páginas específicas mediante nuevos ADRs.

---

## ADR-002 — WhatsApp como CTA principal y llamada como CTA secundario

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

El objetivo comercial es recibir solicitudes de presupuesto y el canal de WhatsApp es especialmente apropiado para iniciar una conversación rápida.

### Decisión

WhatsApp será la llamada a la acción primaria y teléfono la secundaria.

### Alternativas consideradas

- Formulario como CTA principal.
- Email como CTA principal.

### Motivo

Reducir fricción y utilizar los canales ya asociados al contacto directo del profesional.

### Consecuencias

- Los CTAs deben ser visibles en toda la experiencia.
- El formulario no es obligatorio en la primera versión.

---

## ADR-003 — Diseño mobile-first

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

La conversión depende de acciones inmediatas de WhatsApp y llamada, por lo que la experiencia móvil tiene prioridad.

### Decisión

Diseñar y desarrollar mobile-first.

### Alternativas consideradas

- Desktop-first.
- Desktop y mobile diseñados simultáneamente sin prioridad.

### Motivo

La interfaz móvil debe optimizar lectura, contacto y navegación desde el principio.

### Consecuencias

- CTA persistente en móvil.
- Targets táctiles cómodos.
- Desktop se adapta progresivamente.

---

## ADR-004 — Portfolio con fotografías reales como elemento de confianza

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

El profesional dispone de fotografías reales de sus trabajos.

### Decisión

Utilizar fotografías reales como contenido principal de la sección de trabajos y, cuando sea adecuado, en el Hero.

### Alternativas consideradas

- Imágenes de stock.
- Ilustraciones.
- Ausencia de portfolio visual.

### Motivo

Las fotografías reales demuestran capacidad y reducen la percepción de una landing genérica.

### Consecuencias

La calidad, optimización y selección de imágenes pasan a ser parte crítica del producto.

---

## ADR-005 — Reseñas reales de Facebook

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

Existen opiniones reales de clientes en Facebook.

### Decisión

Mostrar reseñas reales seleccionadas y ofrecer un enlace a Facebook para reforzar su verificabilidad.

### Alternativas consideradas

- Testimonios inventados o genéricos.
- No mostrar opiniones.

### Motivo

Las reseñas aportan prueba social real.

### Consecuencias

El contenido debe mantenerse fiel a las reseñas disponibles y no deben inventarse testimonios.

---

## ADR-006 — Servicios agrupados por necesidad

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

El profesional ofrece numerosos servicios y una lista plana sería difícil de escanear.

### Decisión

Agrupar los servicios en:

1. Reformas.
2. Acabados.
3. Instalaciones.
4. Exterior.

### Alternativas consideradas

- Lista plana de servicios.
- Una sección independiente para cada servicio.

### Motivo

Mejora la comprensión y reduce carga cognitiva.

### Consecuencias

No crear una taxonomía más compleja salvo que el contenido futuro lo requiera.

---

## ADR-007 — Propuesta visual: profesionalidad, solidez, limpieza y confianza

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

La web debe representar a un profesional de reformas real, evitando tanto la estética excesivamente industrial como una estética tecnológica.

### Decisión

Utilizar una dirección visual limpia y sólida, apoyada por fotografía real.

Paleta conceptual:

- blanco / crema;
- grafito / carbón;
- gris piedra;
- terracota / naranja de construcción.

### Alternativas consideradas

- Estética industrial pesada.
- Estética startup/tech.
- Diseño genérico basado en una plantilla.

### Motivo

La estética debe generar confianza sin competir visualmente con el portfolio.

### Consecuencias

La fotografía y la tipografía tendrán más peso que los efectos decorativos.

---

## ADR-008 — Arquitectura técnica minimalista

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

El proyecto es una landing estática y no tiene inicialmente necesidades de autenticación, datos persistentes ni lógica de negocio compleja.

### Decisión

No introducir backend, base de datos, estado global o CMS por defecto.

### Alternativas consideradas

- Backend propio.
- CMS.
- Base de datos.
- Arquitectura full-stack.

### Motivo

El coste y la complejidad no están justificados por las necesidades actuales.

### Consecuencias

Si posteriormente se necesita un formulario, analítica, CMS u otra integración, deberá evaluarse individualmente y documentarse en un nuevo ADR.

---

## ADR-009 — Estrategia SEO local desde el inicio

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

La zona de trabajo constituye una parte importante de la intención de búsqueda.

### Decisión

Incluir SEO local en la arquitectura inicial, no como tarea posterior.

### Motivo

Evita tener que rehacer estructura semántica, contenido y metadatos después de desarrollar la UI.

### Consecuencias

El desarrollo debe contemplar headings, metadata, contenido geográfico natural, imágenes y datos estructurados.

---

## ADR-010 — CTA persistente en móvil

**Estado:** Propuesta  
**Fecha:** 2026-08-17

### Contexto

El contacto rápido es el principal objetivo de negocio.

### Decisión

Proponer una barra inferior fija con WhatsApp y llamada.

### Alternativas consideradas

- CTA únicamente dentro del contenido.
- Header sticky sin barra inferior.

### Motivo

Permite iniciar contacto desde cualquier punto de la landing.

### Consecuencias

Debe comprobarse que no tape contenido y que respete safe areas y accesibilidad.

Esta decisión deberá marcarse como `Aceptada` o `Rechazada` tras validación durante el diseño/implementación.

---

## ADR-011 — Formulario como canal secundario

**Estado:** Propuesta  
**Fecha:** 2026-08-17

### Contexto

WhatsApp y teléfono son los canales principales.

### Decisión

El formulario no forma parte obligatoria del MVP. Se añadirá solo si aporta una ventaja demostrable.

### Alternativas consideradas

- Formulario como CTA principal.
- Formulario obligatorio en la landing.

### Motivo

Evitar fricción y evitar introducir backend o terceros innecesarios.

### Consecuencias

Si se implementa, habrá que decidir proveedor, privacidad y tratamiento de datos mediante un ADR específico.

---

# Decisiones pendientes

Estas cuestiones deben resolverse mediante nuevos ADRs cuando se decidan.

## Stack / framework

Decidido en ADR-012: React con Tailwind CSS, compilado como sitio estático y sin backend.

## Estrategia de renderizado

Pendiente de confirmar en función del framework elegido.

La prioridad es static-first o server-rendered cuando aporte ventajas reales.

## Sistema de estilos

Pendiente.

Debe decidirse si se utilizará CSS, CSS Modules, Tailwind u otra solución existente en el proyecto.

## Hosting

Pendiente.

Elegir en función de rendimiento, coste, simplicidad y necesidades del proyecto.

## Analítica

Pendiente.

Debe decidirse proveedor y estrategia de consentimiento antes de integrar scripts de terceros.

## Cookie / privacidad

Pendiente de definición en función de las herramientas externas que se utilicen.

## Schema.org

Pendiente.

Debe seleccionarse el tipo de negocio adecuado según la actividad real y los datos verificables disponibles.

## Google Business Profile

Pendiente de confirmar si existe.

## Nombre / identidad comercial

Pendiente de confirmar.

## Portfolio

Pendiente de selección definitiva de fotografías.

## Reseñas

Pendiente de selección y obtención del contenido final desde Facebook.

## Localidades exactas

Pendiente de definir la lista final de localidades que se mostrarán explícitamente.

---

## ADR-012 — React y Tailwind CSS para una landing estática

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

La landing necesita una base mantenible basada en componentes, estilos consistentes y una entrega sin servicios de servidor.

### Decisión

Utilizar React para estructurar los bloques funcionales de la landing y Tailwind CSS para el sistema de estilos. El resultado se compilará y desplegará como sitio estático, sin backend. No se incorporarán librerías de terceros salvo que una necesidad concreta no pueda resolverse correctamente con las APIs nativas o el stack elegido.

### Alternativas consideradas

- HTML, CSS y JavaScript sin framework.
- Framework con renderizado en servidor.
- Bibliotecas de componentes o utilidades de terceros.

### Motivo

React facilita separar las secciones funcionales sin introducir una arquitectura compleja y Tailwind CSS permite aplicar de forma consistente el diseño mobile-first. La landing no requiere persistencia, autenticación ni lógica de servidor.

### Consecuencias

- El código se organizará en componentes React cohesionados.
- Tailwind CSS será el único sistema de estilos principal.
- Se priorizará una compilación estática con JavaScript cliente mínimo.
- Las dependencias adicionales requerirán una justificación técnica explícita.

---

## ADR-013 — Vite como herramienta de compilación

**Estado:** Aceptada  
**Fecha:** 2026-08-17

### Contexto

La implementación con React y Tailwind CSS necesita un entorno local de desarrollo y una compilación eficiente para una landing estática.

### Decisión

Usar Vite como herramienta de desarrollo y compilación del proyecto React.

### Alternativas consideradas

- Configuración manual de React y bundler.
- Framework con renderizado en servidor.

### Motivo

Vite aporta una configuración pequeña, integración directa con React y Tailwind CSS, y genera una salida estática adecuada para la landing sin añadir un backend.

### Consecuencias

- Los comandos de desarrollo, compilación y previsualización se ejecutarán mediante scripts de Vite.
- La salida de producción será una carpeta estática lista para el hosting elegido.

---

# Regla de mantenimiento

Cada decisión importante tomada durante el desarrollo debe añadirse a este documento en el mismo cambio que la introduce.

El archivo debe funcionar como memoria arquitectónica del proyecto y permitir que otra IA o desarrollador pueda entender **por qué** existe cada decisión relevante, no únicamente **qué** se implementó.
