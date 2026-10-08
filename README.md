# Airflow Lab / Airflow Community Tool

A browser-based, interactive PC airflow visualization tool designed to help users compare fan layouts, cooling configurations, and hardware combinations.

The project runs as a standalone HTML application. It does not require a build step, package manager, backend, or external dependencies.

Language support: Spanish and English.

---

## Español

### Descripción

Airflow Lab es una herramienta comunitaria para visualizar de forma interactiva cómo podría circular el aire dentro de un gabinete de PC según el hardware y la configuración de ventiladores seleccionados.

El programa permite configurar procesador, tarjeta gráfica, refrigeración de CPU, formato del gabinete, placa madre, ventiladores y temperatura ambiente. A partir de esos datos genera una representación 3D ilustrativa con trayectorias de aire, partículas animadas, estimaciones térmicas y balance aproximado entre entrada y extracción.

La interfaz puede cambiarse entre español e inglés desde el selector de idioma de la barra superior. La preferencia queda guardada en el navegador.

### Características principales

- Visualización 3D ilustrativa con proyección ortográfica.
- Vista isométrica, lateral y vista libre mediante rotación manual.
- Zoom con rueda del mouse o controles de la interfaz.
- Trayectorias de flujo animadas.
- Partículas de aire animadas.
- Vectores de velocidad opcionales.
- Transparencia de componentes.
- Corte térmico configurable.
- Coloreado de trayectorias por:
  - velocidad relativa;
  - temperatura estimada del aire.
- Estimación de temperatura del aire cerca de CPU y GPU.
- Estimación de carga térmica de CPU y GPU.
- Evaluación del balance entre ventiladores de entrada y salida.
- Optimizador de ventilación con prioridades de:
  - equilibrio;
  - máximo flujo;
  - menor potencia de ventiladores.
- Configuración independiente de ventiladores frontales, traseros, superiores e inferiores.
- Tamaños de ventilador de 120 mm, 140 mm y 200 mm cuando corresponde.
- Inversión rápida de un grupo de ventiladores haciendo clic sobre el ventilador en la escena.
- Importación y exportación de configuraciones mediante JSON.
- Captura de la simulación en PNG.
- Diseño adaptable para escritorio y dispositivos móviles.
- Interfaz en español e inglés.

### Catálogo de hardware actual

La versión actual incluye aproximadamente:

- 55 procesadores AMD e Intel.
- 61 tarjetas gráficas NVIDIA, AMD e Intel Arc.
- 12 opciones de refrigeración de CPU.
- 4 tipos genéricos de gabinete.

El catálogo incluye procesadores AMD Ryzen desde la serie 3000 y varias generaciones equivalentes de Intel, además de distintas generaciones de GPU NVIDIA GeForce, AMD Radeon e Intel Arc.

### Refrigeración compatible

El simulador incluye configuraciones como:

- cooler stock genérico;
- AMD Wraith;
- Intel Laminar;
- torres de aire de 92 mm, 120 mm y 140 mm;
- doble torre;
- AIO de 120 mm, 240 mm, 280 mm, 360 mm y 420 mm.

Los AIO pueden colocarse en posiciones compatibles del modelo, como frontal o superior.

### Cómo ejecutar el proyecto

No se necesita instalación.

1. Descarga o clona el repositorio.
2. Abre `index.html` en un navegador moderno.

También puedes usar un servidor local sencillo. Por ejemplo, con Python:

```bash
python -m http.server 8000
```

Después abre:

```text
http://localhost:8000
```

### Publicar con GitHub Pages

Como el proyecto es completamente estático, puede publicarse directamente con GitHub Pages.

1. Sube `index.html` y `README.md` al repositorio.
2. Abre la configuración del repositorio en GitHub.
3. Entra en `Pages`.
4. Selecciona `Deploy from a branch`.
5. Selecciona la rama `main` y la carpeta raíz `/`.
6. Guarda los cambios.

### Controles

- Arrastrar sobre la escena: girar la vista.
- Rueda del mouse: zoom.
- Clic sobre un ventilador: invertir el grupo de entrada/salida.
- Flechas del teclado: girar la cámara.
- `+` y `-`: zoom.
- Barra espaciadora: pausar o reanudar la animación.

### Importar y exportar configuraciones

La configuración puede exportarse como JSON desde la interfaz. Esto permite compartir un setup, guardarlo o usarlo como base para comparar distintas configuraciones.

Ejemplo simplificado:

```json
{
  "caseType": "mid",
  "mbType": "ATX",
  "ambient": 24,
  "cpuSelect": "r5-5500",
  "coolerSelect": "tower120",
  "gpuSelect": "rtx3060",
  "frontCount": 3,
  "frontMode": "intake",
  "rearCount": 1,
  "rearMode": "exhaust"
}
```

### Limitaciones importantes

Airflow Lab no es un solver CFD validado y no debe interpretarse como sustituto de SolidWorks Flow Simulation, ANSYS Fluent, OpenFOAM u otras herramientas de ingeniería.

La simulación utiliza un modelo cualitativo e ilustrativo. Las trayectorias, velocidades relativas y temperaturas se utilizan para comparar configuraciones dentro de la propia herramienta.

Las cifras de temperatura representan aire estimado cerca de los componentes, no la temperatura real del chip, hotspot, VRAM, VRM o sensor interno.

Los resultados reales dependen de muchos factores que el modelo simplifica, entre ellos:

- geometría exacta del gabinete;
- restricciones del panel frontal;
- filtros de polvo;
- curvas reales de presión y flujo de cada ventilador;
- turbulencia tridimensional;
- disipadores específicos de cada GPU;
- posición y forma del cableado;
- presión estática del radiador;
- temperatura real de los componentes;
- orientación física del equipo.

La herramienta debe utilizarse como ayuda para comparar configuraciones y comprender el flujo de aire, no como medición de ingeniería.

### Estructura del repositorio

```text
/
├── index.html
└── README.md
```

Actualmente toda la aplicación está contenida en un solo archivo HTML para facilitar su distribución, modificación y publicación.

### Ideas para próximas versiones

- Base de datos de gabinetes reales con dimensiones y restricciones.
- Modelos específicos de tarjetas gráficas por ensamblador.
- Base de datos de ventiladores con CFM, RPM y presión estática.
- Modelado de filtros antipolvo y paneles mesh.
- Curvas PWM personalizadas.
- Comparación A/B entre dos configuraciones.
- Guardado de configuraciones mediante enlaces compartibles.
- Galería comunitaria de setups.
- Perfiles de radiadores con distinta resistencia al flujo.
- Motor de simulación de fluidos más avanzado.
- Persistencia opcional mediante una base de datos.

### Contribuciones

Las contribuciones son bienvenidas.

Algunas formas de colaborar:

- agregar hardware;
- mejorar los datos térmicos aproximados;
- corregir traducciones;
- mejorar accesibilidad;
- mejorar compatibilidad móvil;
- reportar errores;
- proponer mejoras del modelo de flujo;
- añadir nuevos tipos de gabinete o refrigeración.

Para cambios grandes, se recomienda abrir primero un issue explicando la propuesta.

### Licencia

Este repositorio no incluye una licencia automáticamente. Antes de distribuir el proyecto como software abierto, agrega un archivo `LICENSE` con la licencia que quieras utilizar.

---

## English

### Overview

Airflow Lab is a community-oriented tool for interactively visualizing how air may move inside a PC case based on the selected hardware and fan configuration.

Users can configure the processor, graphics card, CPU cooling solution, case format, motherboard, fans, and ambient temperature. The application then generates an illustrative 3D representation with airflow paths, animated particles, thermal estimates, and an approximate intake/exhaust balance.

The interface can be switched between Spanish and English using the language selector in the top bar. The selected language is stored locally in the browser.

### Main features

- Illustrative 3D visualization with orthographic projection.
- Isometric, side, and free camera views.
- Mouse-wheel zoom and interface zoom controls.
- Animated airflow paths.
- Animated air particles.
- Optional velocity vectors.
- Component transparency mode.
- Adjustable thermal slice.
- Airflow path coloring by:
  - relative speed;
  - estimated air temperature.
- Estimated air temperature near the CPU and GPU.
- Estimated CPU and GPU thermal load.
- Approximate intake/exhaust fan balance.
- Airflow optimizer with priorities for:
  - balanced operation;
  - maximum airflow;
  - lower fan power.
- Independent configuration for front, rear, top, and bottom fan groups.
- 120 mm, 140 mm, and 200 mm fan sizes where supported.
- Click a fan in the scene to reverse its entire fan group.
- Import and export configurations as JSON.
- PNG simulation capture.
- Responsive desktop and mobile layout.
- Spanish and English interface.

### Current hardware catalog

The current version includes approximately:

- 55 AMD and Intel processors.
- 61 NVIDIA, AMD, and Intel Arc graphics cards.
- 12 CPU cooling options.
- 4 generic case types.

The catalog includes AMD Ryzen processors starting with the Ryzen 3000 family and several equivalent Intel generations, as well as multiple NVIDIA GeForce, AMD Radeon, and Intel Arc GPU generations.

### Supported cooling configurations

The simulator includes options such as:

- generic stock cooler;
- AMD Wraith;
- Intel Laminar;
- 92 mm, 120 mm, and 140 mm air towers;
- dual-tower air cooling;
- 120 mm, 240 mm, 280 mm, 360 mm, and 420 mm AIO liquid coolers.

AIO radiators can be placed in supported positions in the generic case model, such as the front or top.

### Running the project

No installation is required.

1. Download or clone the repository.
2. Open `index.html` in a modern browser.

You can also run a simple local web server. For example, with Python:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

### Deploying with GitHub Pages

Because the project is fully static, it can be hosted directly with GitHub Pages.

1. Upload `index.html` and `README.md` to the repository.
2. Open the repository settings on GitHub.
3. Open `Pages`.
4. Select `Deploy from a branch`.
5. Select the `main` branch and the root `/` folder.
6. Save the configuration.

### Controls

- Drag on the scene: rotate the view.
- Mouse wheel: zoom.
- Click a fan: reverse the selected fan group.
- Arrow keys: rotate the camera.
- `+` and `-`: zoom.
- Space bar: pause or resume the animation.

### Importing and exporting configurations

The system configuration can be exported as JSON from the interface. This makes it possible to share a setup, save it, or use it as the basis for comparing different airflow configurations.

Simplified example:

```json
{
  "caseType": "mid",
  "mbType": "ATX",
  "ambient": 24,
  "cpuSelect": "r5-5500",
  "coolerSelect": "tower120",
  "gpuSelect": "rtx3060",
  "frontCount": 3,
  "frontMode": "intake",
  "rearCount": 1,
  "rearMode": "exhaust"
}
```

### Important limitations

Airflow Lab is not a validated CFD solver and should not be treated as a replacement for SolidWorks Flow Simulation, ANSYS Fluent, OpenFOAM, or other engineering simulation tools.

The application uses a qualitative, illustrative model. Airflow paths, relative velocities, and thermal estimates are intended mainly for comparing configurations inside the tool.

Displayed temperatures represent estimated air near the components, not actual chip, hotspot, VRAM, VRM, or internal sensor temperatures.

Real-world results depend on many factors that are simplified by the current model, including:

- exact case geometry;
- front-panel restrictions;
- dust filters;
- real fan pressure/flow curves;
- three-dimensional turbulence;
- specific GPU heatsink geometry;
- cable placement;
- radiator static-pressure resistance;
- actual component temperatures;
- physical orientation of the system.

The tool should be used as an educational and comparative airflow aid rather than an engineering measurement system.

### Repository structure

```text
/
├── index.html
└── README.md
```

The complete application currently lives in a single HTML file to keep distribution, modification, and deployment simple.

### Possible future development

- Database of real PC cases with dimensions and airflow restrictions.
- Board-partner-specific graphics card models.
- Fan database with CFM, RPM, and static pressure.
- Dust filter and mesh resistance modeling.
- Custom PWM fan curves.
- A/B comparison between two configurations.
- Shareable configuration links.
- Community setup gallery.
- Radiator profiles with different airflow resistance.
- More advanced fluid simulation engine.
- Optional database-backed persistence.

### Contributing

Contributions are welcome.

Useful areas for contribution include:

- adding hardware;
- improving approximate thermal data;
- correcting translations;
- accessibility improvements;
- mobile compatibility;
- bug reports;
- airflow model improvements;
- additional case and cooling configurations.

For larger changes, consider opening an issue first to describe the proposal.

### License

This repository does not automatically include a license. Before distributing the project as open-source software, add a `LICENSE` file containing the license you want to use.
