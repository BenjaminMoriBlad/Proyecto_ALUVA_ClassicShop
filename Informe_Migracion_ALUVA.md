# INFORME DE MIGRACIÓN DE PÁGINA WEB A TEMPLATE ESTÁNDAR
## PROYECTO ALUVA - INDUMENTARIA TÉCNICA Y EPP

---

### PORTADA

* **Institución:** Instituto Profesional IPLACEX  
* **Escuela:** Escuela de Informática y Telecomunicaciones  
* **Asignatura:** Diseño Web  
* **Unidad:** Unidad III - Introducción a JavaScript / Uso de Plantillas  
* **Evaluación:** Evaluación N°3 - Migración a Template Estándar  
* **Proyecto:** ALUVA (Ropa de Trabajo y Elementos de Protección Personal)  
* **Template Seleccionado:** Classic Shop (Assan v3.8 - Bootstrap 4)  
* **Grupo:** Sebastián Donoso Aliaga, Brunno Mori Campos, Hugo González Alarcón y Víctor Maureira Flores
* **Fecha de Entrega:** 14 de Septiembre 2026  

---

### 1. INTRODUCCIÓN

El presente informe documenta detalladamente el proceso de migración y expansión del sitio web corporativo y de comercio electrónico de la empresa **ALUVA** —especializada en vestuario técnico faenero, ropa de trabajo y Equipos de Protección Personal (EPP)— desde su diseño base (desarrollado en la Evaluación N°2) hacia un template web estándar y profesional de arquitectura modular.

El objetivo central de esta actividad es elevar los estándares de diseño, responsividad y experiencia de usuario (UX/UI) incorporando la plantilla estándar de la industria **Classic Shop** (de la suite Assan v3.8 / Bootstrap 4). En esta versión expandida, se ha incorporado el **logo oficial de la marca**, los **testimonios reales de clientes** y la **totalidad del Catálogo Oficial ALUVA 2026** compuesto por XX productos clasificados en categorías (Polerones & Chaquetas, Camisas & Blusas, Pantalones Cargo, Primera Capa y Accesorios & EPP), manteniendo la integración interactiva con el Carrito de Compras en `localStorage` y el Módulo Logístico de Rastreo.

---

### 2. DESCRIPCIÓN DEL TEMPLATE SELECCIONADO Y RAZONES DE SU ELECCIÓN

#### 2.1 Descripción del Template "Classic Shop"
El template **Classic Shop** forma parte del ecosistema de plantillas profesionales *Assan v3.8*, construido sobre la base del framework responsivo **Bootstrap 4**. Entre sus principales características destacan:

* **Arquitectura Grid Responsiva de 12 Columnas:** Garantiza adaptabilidad fluida en dispositivos móviles, tablets y monitores de alta resolución.
* **Barra Superior (Top Bar) Corporativa:** Espacio dedicado a datos de contacto rápido (correo, dirección), accesos a redes sociales con íconos vectoriales simétricos para Instagram y TikTok.
* **Navegación Header Sticky con Marca Oficial:** Menú de navegación colapsable para smartphones con el isotipo/logo oficial de ALUVA y botón de carrito interactivo.
* **Menú Off-Canvas / Pushy Drawer para Comercio Electrónico:** Panel lateral desplegable (*"Tu Pedido"*) activado exclusivamente por click que muestra el desglose del pedido sin interrumpir la navegación.
* **Botón Flotante de WhatsApp:** Acceso directo para personalización de prendas y cotizaciones corporativas.

#### 2.2 Razones de su Elección
1. **Alineación con el Negocio (E-Commerce Industrial):** La estructura visual de *Classic Shop* está nativamente orientada al comercio electrónico de indumentaria, ofreciendo tarjetas de producto limpias, badges de tela y botones de compra directos.
2. **Excelente UX/UI Móvil:** La inclusión del drawer lateral off-canvas y botones de filtro interactivos resuelve de forma elegante la navegación en pantallas pequeñas.
3. **Escalabilidad y Mantenibilidad:** Permite sobreescribir estilos mediante una hoja de personalización propia (`custom-aluva.css`) manteniendo la integridad de la grilla.

---

### 3. PASOS SEGUIDOS EN LA MIGRACIÓN Y EXPANSIÓN DE CONTENIDOS

El proceso se ejecutó en 5 etapas estructuradas:

#### Paso 1: Importación de Recursos Oficiales del Emprendimiento
Se integró el material oficial del emprendimiento desde la Unidad 1:
* **Logotipo Oficial:** Se configuró `LOGO ALUVA.jpeg` en el encabezado principal y `ALUVA TIMBRE.jpeg` en el pie de página.
* **Catálogo Completo 2026:** Se procesó el archivo `CATÁLOGO ALUVA 2026.pdf` extrayendo los XX productos con sus códigos de referencia, tallas, precios en CLP y especificaciones técnicas.

#### Paso 2: Maquetación y Filtros Interactivos en Catálogo (`catalogo.html`)
* Se implementó una barra de botones de filtro interactivo (*Todos*, *Polerones & Chaquetas*, *Camisas & Blusas*, *Pantalones Cargo*, *Primera Capa*, *Accesorios & EPP*) coordinada por JavaScript (`initCatalogFilters()`).
* Cada tarjeta de producto incluye su código de referencia (ej: *Ref: 06052*), badge de tela/talla, precio en CLP y botón *"Añadir al Carrito"*.

#### Paso 3: Estilización y Armonía Visual (`custom-aluva.css`)
* **Simetría de Redes Sociales:** Los íconos de Instagram y TikTok se configuraron en círculos identitarios de **32px × 32px** con SVG vectoriales e interacción de hover propia.
* **Alineación de Encabezado:** El ícono de correo se integró en línea recta horizontal previo a la dirección `aluva.seguridad@gmail.com`.
* **Botón Flotante WhatsApp:** Integración fija en la esquina inferior derecha para cotización directa.

#### Paso 4: Refactorización de JavaScript
* **Carrito Off-Canvas (`cart.js`):** Ajustado para desplegarse **exclusivamente mediante click** en la bolsa de compras o al presionar *"Añadir"*, evitando cierres o desplazamientos involuntarios por pasar el ratón.
* **Tracking Logístico (`tracking.js`):** Soporte para envíos Starken, Chilexpress, Correos de Chile y UPS.

#### Paso 5: QA y Verificación de Responsividad
Pruebas exhaustivas en distintas resoluciones, verificando el filtrado instantáneo de productos y el almacenamiento en `localStorage`.

---

### 4. CAPTURAS DE PANTALLA Y ANÁLISIS COMPARATIVO


---

### 5. PROBLEMAS ENCONTRADOS Y CÓMO SE RESOLVIERON

#### Problema 1: Desalineación de Íconos de Redes Sociales en la Top Bar
* **Descripción:** Al usar un ícono FontAwesome para Instagram y un SVG para TikTok, existían diferencias de tamaño y desalineación vertical.
* **Solución:** Se unificaron ambos botones dentro de la clase `.top-social-circle` en elementos circulares idénticos de 32px × 32px con SVG vectoriales de 14px × 14px y efectos hover diferenciados por marca.

#### Problema 2: Apertura Involuntaria del Carrito al Mover el Cursor
* **Descripción:** La activación por evento hover abría el drawer lateral de forma invasiva mientras el usuario navegaba por el menú principal.
* **Solución:** Se reescribió `cart.js` y `custom-aluva.css` para restringir la apertura y cierre del panel de *"Tu Pedido"* a **eventos explícitos de click**.

#### Problema 3: Clasificación de los XX Productos del Catálogo 2026
* **Descripción:** Renderizar XX tarjetas de producto podía saturar la vista móvil.
* **Solución:** Se creó un sistema de pestañas de filtrado en JavaScript que oculta o muestra dinámicamente las tarjetas según la categoría seleccionada sin recargar la página.

---

### 6. APORTE INDIVIDUAL

En esta versión expandida, los estudiantes realizaron las siguientes tareas técnicas y organizativas:

* **Extracción y Procesamiento de Información:** Análisis de la documentación e imágenes de la Unidad 1 (`Información emprendimiento ALUVA.docx` y `CATÁLOGO ALUVA 2026.pdf`), extrayendo los XX productos con sus códigos de referencia y características.
* **Desarrollo Frontend y Filtros JS:** Construcción de la grilla completa del catálogo y programación de la función `initCatalogFilters()` para filtrado por categoría.
* **Diseño e Identidad Visual:** Implementación del logotipo oficial, estilización armoniosa de botones sociales en la Top Bar y adición del botón flotante de WhatsApp.
* **Optimización de UX/UI:** Ajuste del control de estado por click para el drawer de carrito.
* **Actualización Documental:** Elaboración y actualización completa de este informe formal de migración.

---

### 7. CONCLUSIÓN

La migración y expansión del sitio web de **ALUVA** hacia el template **Classic Shop** representa un salto cualitativo integral. La plataforma ahora cuenta con XX productos del Catálogo 2026, filtrado por categorías, logo oficial, y un sistema de cotización directa por WhatsApp, consolidando una tienda virtual completa, responsiva y lista para operaciones comerciales reales.
