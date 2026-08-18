# Especificación técnica — Landing de reformas

## 1. Propósito

Este documento define los requisitos técnicos de la landing page de un profesional de reformas que trabaja principalmente en Alhama de Murcia y, según el trabajo, en Murcia, Lorca y localidades cercanas.

La aplicación es una **landing de conversión**, no una aplicación de gestión. La prioridad técnica es entregar una página rápida, accesible, indexable y fácil de mantener.

---

## 2. Objetivos técnicos

- Priorizar rendimiento, especialmente en móvil.
- Mantener una arquitectura sencilla y justificable.
- Facilitar cambios de contenido sin modificar lógica innecesariamente.
- Implementar HTML semántico.
- Cumplir buenas prácticas de accesibilidad.
- Preparar SEO local desde el inicio.
- Medir conversiones de WhatsApp y teléfono.
- Evitar dependencias innecesarias.
- Evitar una arquitectura de frontend sobredimensionada para una única landing.

---

## 3. Estado del stack

El stack confirmado es React con Tailwind CSS, compilado como una landing estática y sin backend. No se añadirán librerías de terceros salvo que exista una necesidad técnica concreta que no pueda cubrirse con las APIs nativas o este stack.

### Criterios de implementación

- React para componentes funcionales cohesionados que representen bloques reales de la landing.
- Tailwind CSS como sistema principal de estilos mobile-first.
- Compilación estática con JavaScript cliente mínimo.
- Sin backend, base de datos, autenticación ni servicios remotos propios.

Si se utiliza TypeScript, mantener:

- TypeScript con `strict` habilitado.
- Tipos explícitos en props y modelos de contenido.
- `type` en lugar de `interface`, salvo una necesidad técnica concreta.
- Prohibido `any`.
- Componentes pequeños y cohesionados.

La decisión se registra en `ARCHITECTURE_DECISIONS.md` mediante ADR-012; el bundler y el hosting permanecen pendientes de selección.

---

## 4. Naturaleza de la aplicación

No se necesita inicialmente:

- Backend propio.
- Base de datos.
- Sistema de usuarios.
- CMS obligatorio.
- Panel de administración.
- API propia.
- Autenticación.
- Estado global.

El contenido inicial es principalmente estático: textos, servicios, portfolio, reseñas y datos de contacto.

Solo añadir una infraestructura adicional si existe una necesidad real y documentada.

---

## 5. Estructura funcional

La página debe organizarse en una única ruta principal, salvo que aparezca una necesidad real que justifique páginas adicionales.

Orden recomendado:

```text
Header
Hero
Servicios
Trabajos realizados
Por qué elegirme
Cómo trabajo
Opiniones
Zona de trabajo
CTA final
Footer
```

La navegación interna debe utilizar anchors semánticos.

---

## 6. Componentización

La estructura de componentes debe reflejar bloques funcionales y no dividir arbitrariamente cada elemento visual.

Ejemplo conceptual:

```text
LandingPage
├── Header
├── HeroSection
├── ServicesSection
├── PortfolioSection
├── TrustSection
├── ProcessSection
├── ReviewsSection
├── ServiceAreaSection
├── FinalCtaSection
└── Footer
```

Los nombres reales dependerán del framework y de las convenciones del proyecto.

### Regla

Crear un componente cuando:

- tenga una responsabilidad clara;
- tenga reutilización real o prevista razonablemente;
- reduzca complejidad;
- facilite mantenimiento o testing.

No crear wrappers ni abstracciones únicamente para reducir líneas de código.

---

## 7. Modelo de contenido

Cuando sea práctico, separar el contenido de la estructura visual.

Ejemplo conceptual:

```ts
type ServiceCategory = {
  title: string;
  items: string[];
};

type Project = {
  title: string;
  description?: string;
  image: string;
  alt: string;
};

type Review = {
  author: string;
  text: string;
  rating?: number;
  source: string;
};
```

No inventar campos innecesarios. El modelo debe corresponder al contenido real disponible.

---

## 8. Datos de negocio confirmados

- Experiencia: 10 años.
- Compra de materiales: sí.
- Zona principal: Alhama de Murcia.
- Desplazamiento: Murcia y Lorca aproximadamente según el trabajo.
- Portfolio: fotografías reales disponibles.
- Reseñas: disponibles en Facebook.
- Presupuesto: sin compromiso.
- Teléfono / WhatsApp: `+34 643 93 26 83`.

No añadir datos comerciales no confirmados.

---

## 9. Servicios

### Reformas

- Reformas integrales.
- Reformas de baños.
- Reformas de interiores.

### Acabados

- Pintura interior.
- Pintura exterior.
- Pintura decorativa.
- Alisado de paredes.
- Colocación de azulejos.
- Pladur.

### Instalaciones

- Fontanería.
- Electricidad.
- Puertas y ventanas.
- Falsos techos.
- Paneles sándwich.

### Exterior

- Jardinería.
- Otros trabajos de exterior únicamente si se confirman.

---

## 10. Conversión

### CTA principal

WhatsApp.

### CTA secundario

Llamada telefónica.

Todo botón de WhatsApp debe abrir el canal correcto mediante un enlace bien formado y accesible. El número debe mantenerse en un único origen de datos cuando sea posible.

La llamada debe utilizar un enlace `tel:` en dispositivos compatibles.

No esconder ambos canales detrás de un menú o un formulario.

---

## 11. CTA persistente en móvil

Se recomienda una barra inferior fija con:

```text
WhatsApp | Llamar
```

Requisitos:

- No tapar contenido importante.
- Respetar safe areas de dispositivos móviles.
- Mantener contraste suficiente.
- Mantener targets táctiles cómodos.
- Tener estados `focus-visible` claros.

---

## 12. Formularios

El formulario es secundario y debe implementarse únicamente si aporta valor real.

Campos previstos:

- Nombre.
- Teléfono.
- Necesidad / tipo de reforma.
- Mensaje.

No añadir email obligatorio ni datos innecesarios sin una justificación funcional.

Si el formulario requiere backend o un servicio externo, esa decisión debe registrarse antes de introducir la integración.

---

## 13. Imágenes

Las imágenes reales de trabajos son un activo central de la página.

Requisitos técnicos:

- Utilizar formatos modernos cuando sea compatible.
- Servir tamaños adecuados al viewport.
- Usar `width` y `height` o mecanismos equivalentes para evitar layout shift.
- Utilizar `loading="lazy"` en imágenes fuera del viewport inicial cuando corresponda.
- No aplicar lazy loading indiscriminado al elemento visual principal del Hero.
- `alt` descriptivo y útil.
- Evitar alt redundante o keyword stuffing.

Las imágenes no deben perder calidad de forma innecesaria.

---

## 14. Accesibilidad

Objetivo mínimo: WCAG 2.2 AA como referencia de implementación, priorizando los criterios relevantes para una landing.

Requisitos:

- HTML semántico.
- Jerarquía correcta de headings.
- Un H1 principal.
- Navegación accesible por teclado.
- `focus-visible` visible.
- Contraste suficiente.
- Botones y enlaces identificables.
- No depender exclusivamente del color.
- Texto alternativo para imágenes informativas.
- Enlaces de contacto comprensibles fuera de contexto cuando sea necesario.
- Respetar `prefers-reduced-motion` si se introducen animaciones.

---

## 15. SEO on-page

### Principales consultas objetivo

- reformas en Alhama de Murcia
- reformista en Alhama de Murcia
- empresa de reformas en Alhama de Murcia
- reformas de baños en Alhama de Murcia
- pintor en Alhama de Murcia
- albañil en Alhama de Murcia
- reformas en Murcia
- reformas en Lorca

No realizar keyword stuffing.

### Requisitos

- `title` único y descriptivo.
- `meta description` relevante.
- Un único H1.
- H2/H3 con jerarquía lógica.
- Contenido geolocalizado de forma natural.
- `alt` descriptivos.
- Canonical si el stack lo requiere.
- Open Graph / social metadata.
- `robots.txt` y sitemap cuando corresponda al sistema de despliegue.
- Schema.org adecuado al tipo de negocio real.

No afirmar una categoría empresarial concreta de Schema.org hasta comprobar cuál representa correctamente el negocio.

---

## 16. Datos estructurados

La implementación debe considerar Schema.org para un negocio local.

Antes de decidir el tipo exacto, comprobar:

- Qué categoría de negocio corresponde realmente.
- Qué datos están disponibles de forma verificable.
- Qué campos exige o recomienda el tipo elegido.

Nunca introducir datos estructurados ficticios solo para enriquecer el resultado.

---

## 17. Rendimiento

Prioridades:

1. LCP rápido.
2. CLS bajo.
3. JS mínimo.
4. Imágenes correctamente dimensionadas.
5. Fuentes optimizadas.
6. Evitar librerías grandes para interacciones pequeñas.
7. Reducir código cliente cuando el framework lo permita.

Toda animación debe justificar su coste.

---

## 18. Diseño responsive

Enfoque mobile-first.

Breakpoints concretos no están fijados todavía. Deben elegirse según el contenido y no por seguir un sistema de breakpoints arbitrario.

Validar como mínimo:

- móvil pequeño;
- móvil grande;
- tablet;
- desktop.

---

## 19. Dirección visual

La UI debe comunicar:

- Profesionalidad.
- Solidez.
- Limpieza.
- Confianza.

Paleta conceptual:

- blanco / crema;
- grafito / carbón;
- gris piedra;
- terracota / naranja de construcción como acento.

Tipografía:

- sans-serif legible;
- headings con peso suficiente;
- body cómodo en móvil;
- CTA con peso visual claro.

No utilizar una estética excesivamente tecnológica ni genéricamente industrial.

---

## 20. Analítica

Medir como mínimo:

- visitas;
- clicks en WhatsApp;
- clicks en teléfono;
- envíos del formulario, si existe.

Los eventos concretos, proveedor de analítica y estrategia de privacidad son decisiones pendientes y deben documentarse antes de integrar herramientas externas.

---

## 21. Privacidad y cumplimiento

Si se incorpora analítica, formularios, cookies de terceros o cualquier servicio externo, revisar las obligaciones legales aplicables antes del despliegue.

No asumir que una herramienta puede instalarse sin analizar consentimiento, cookies y tratamiento de datos.

---

## 22. Testing

Como mínimo:

- Validación funcional de todos los CTAs.
- Navegación por teclado.
- Validación de enlaces `tel:` y WhatsApp.
- Validación de responsive.
- Validación de headings.
- Comprobación de imágenes rotas.
- Comprobación de metadatos SEO.
- Lighthouse/PageSpeed como herramienta de revisión, no como único criterio.

Los componentes interactivos complejos, si aparecen, deberán tener tests apropiados.

---

## 23. Criterios de aceptación técnicos

La implementación se considera técnicamente correcta cuando:

- funciona en móvil y desktop;
- los CTAs de WhatsApp y llamada funcionan;
- el contenido es accesible por teclado;
- las imágenes no provocan problemas graves de layout;
- no existen errores de consola relevantes;
- el HTML es semántico;
- el SEO básico está implementado;
- el contenido real no contiene afirmaciones inventadas;
- el código mantiene una complejidad proporcional a una landing de una sola página;
- las decisiones técnicas importantes están registradas en `ARCHITECTURE_DECISIONS.md`.
