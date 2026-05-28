# README — Aplicación Local de Mapa de Calor WiFi

## Descripción general

Esta aplicación permite crear un mapa de calor WiFi completamente local utilizando un plano de la empresa en formato PNG/JPG y los datos reales recogidos manualmente de los Access Points.

La herramienta está diseñada para:

* Visualizar cobertura WiFi real.
* Analizar zonas muertas.
* Comparar cobertura 2.4 GHz y 5 GHz.
* Escalar correctamente el plano según medidas reales.
* Trabajar completamente offline.
* Exportar e importar proyectos.

La aplicación no utiliza ningún servidor ni realiza conexiones externas. Para ello, es necesario descargar todos los archivos del repositorio. En caso de que no quieras descargar el archivo "xlsx.full.min.js"
no es estrictamente necesario, pero para ello, tendrás que modificar el código, cambiando la dirección local donde apunta la línea 9 por la dirección "https://cdn.jsdelivr.net/npm/xlsx/dist/xlsx.full.min.js"
pero si lo haces, ya estás haciendo una conexión con un servidor externo (que aunque es 100% seguro, la idea es que esta aplicación funcione sin conexión de ningún tipo, haciéndolo completamente blindado a 
posibles ataques y amenazas externas).

\------------------------------------------------------------------------------------

# Características principales

## 1\. Carga de plano

Permite cargar:

* PNG
* JPG
* WEBP

El plano se muestra automáticamente en el canvas principal.

\------------------------------------------------------------------------------------

## 2\. Sistema de escalado real

La aplicación incorpora un sistema de escalado para que las distancias del mapa correspondan a metros reales.

### Funcionamiento

1. Pulsar:

```text
Activar modo escala
```

2. Seleccionar dos puntos sobre el plano.
3. Introducir la distancia real entre esos dos puntos.

Ejemplo:

```text
Distancia real: 10 metros
```

La aplicación calculará automáticamente:

```text
Pixels por metro
```

Esto permite:

* Que las interpolaciones de cobertura sean reales.
* Que los cálculos de señal respeten las dimensiones físicas.
* Obtener un mapa de calor mucho más preciso.

\------------------------------------------------------------------------------------

# 3\. Creación de Access Points

Cada Access Point puede almacenarse con:

|Campo|Descripción|
|-|-|
|Nombre|Nombre identificativo del AP|
|IP|Dirección IP|
|MAC|Dirección MAC|
|Modelo|Modelo del dispositivo|
|Área|Zona o departamento|

\------------------------------------------------------------------------------------

# 4\. Posicionamiento de APs

## Cómo colocar un AP

1. Completar los datos del Access Point.
2. Pulsar:

```text
Seleccionar posición en mapa
```

3. Hacer click sobre el plano.

El AP quedará fijado en esa posición.

\------------------------------------------------------------------------------------

# 5\. Introducción de medidas WiFi

La aplicación permite introducir datos reales medidos para:

* 2.4 GHz
* 5 GHz

Y para cada banda:

|Distancia|Direcciones|
|-|-|
|5 metros|Arriba / Abajo / Izquierda / Derecha|
|10 metros|Arriba / Abajo / Izquierda / Derecha|

\------------------------------------------------------------------------------------

# 6\. Cómo introducir los dBm

Se deben introducir valores negativos.

Ejemplos habituales:

|Calidad|dBm|
|-|-|
|Excelente|-30|
|Muy buena|-45|
|Buena|-60|
|Regular|-75|
|Mala|-90|

Ejemplo:

```text
↑ 5m = -55
↓ 5m = -60
← 5m = -58
→ 5m = -63
```

\------------------------------------------------------------------------------------

# 7\. Generación del mapa de calor

La aplicación genera automáticamente una interpolación visual utilizando:

* La posición física del AP.
* La distancia.
* Las medidas reales.
* La escala del plano.

## Colores del mapa

|Color|Intensidad|
|-|-|
|Azul|Señal excelente|
|Verde|Señal buena|
|Amarillo|Señal media|
|Naranja|Señal baja|
|Rojo|Señal muy débil|

\------------------------------------------------------------------------------------

# 8\. Visualización por banda

La aplicación permite cambiar entre:

* 2.4 GHz
* 5 GHz

Utilizando los botones:

```text
Ver 2.4 GHz
Ver 5 GHz
```

Esto permite comparar fácilmente:

* Alcance.
* Intensidad.
* Cobertura.
* Diferencias entre bandas.

\------------------------------------------------------------------------------------

# 9\. Gestión de Access Points

La lista lateral muestra:

* Nombre.
* Área.
* IP.
* MAC.
* Modelo.
* Posición.

También permite:

```text
Eliminar AP individual
```

Y:

```text
Eliminar todos los APs
```

\------------------------------------------------------------------------------------

# 10\. Exportación de proyectos

La aplicación puede guardar el proyecto completo en formato JSON.

## Qué se guarda

* Todos los Access Points.
* Posiciones.
* Medidas.
* Escala.
* Configuración.

## Cómo exportar

Pulsar:

```text
Exportar proyecto JSON
```

\------------------------------------------------------------------------------------

# 11\. Importación de proyectos

Permite recuperar proyectos previamente guardados.

## Cómo importar

1. Pulsar:

```text
Seleccionar archivo JSON
```

2. Elegir el archivo exportado.

La aplicación restaurará automáticamente:

* APs.
* Posiciones.
* Coberturas.
* Escala.

\------------------------------------------------------------------------------------

# 12\. Funcionamiento offline

La aplicación:

* NO usa internet.
* NO usa APIs externas.
* NO envía datos.
* NO necesita backend.
* NO utiliza bases de datos remotas.

Todo se ejecuta directamente en el navegador.

\------------------------------------------------------------------------------------

# 13\. Cómo ejecutar la aplicación

## Opción 1 — Abrir directamente

1. Guardar el archivo:

```text
index.html
```

2. Abrirlo con:
* Chrome
* Edge
* Firefox
* Brave

\------------------------------------------------------------------------------------

## Opción 2 — Servidor local opcional

También puede ejecutarse mediante un servidor local.

Ejemplo con Python:

```bash
python -m http.server 8080
```

Después abrir:

```text
http://localhost:8080
```

\------------------------------------------------------------------------------------

# 14\. Recomendaciones de uso

## Para obtener mejores resultados

### Escala

* Escalar siempre el plano.
* Utilizar distancias largas para mejorar precisión.

### Mediciones

* Medir con el mismo dispositivo.
* Mantener la misma altura.
* Evitar cambios durante las pruebas.

### Señal

* Introducir valores reales.
* No redondear demasiado.

### Planos

* Utilizar imágenes de alta resolución.
* Mantener proporciones reales.

\------------------------------------------------------------------------------------

# 15\. Posibles mejoras futuras

La aplicación puede ampliarse con:

* Muestreo radial completo.
* Soporte para paredes y materiales.
* Atenuación automática.
* Exportación PDF.
* Informes automáticos.
* Cobertura multi-planta.
* Predicción de roaming.
* Detección de solapamientos.
* Canales WiFi.
* Potencia configurable.
* Zoom avanzado.
* Mini mapa.
* Guardado automático.
* SQLite local.

\------------------------------------------------------------------------------------

# 16\. Estructura técnica

## Tecnologías utilizadas

|Tecnología|Uso|
|-|-|
|HTML5|Interfaz|
|CSS3|Diseño|
|JavaScript Vanilla|Lógica|
|Canvas API|Renderizado del mapa|

\---

# 17\. Algoritmo del mapa de calor

El sistema calcula:

1. Distancia entre el punto y cada AP.
2. Dirección respecto al AP.
3. Intensidad correspondiente.
4. Interpolación entre 5m y 10m.
5. Atenuación progresiva.
6. Señal más fuerte de todos los APs.

Finalmente se colorea cada celda del canvas.

\------------------------------------------------------------------------------------

# 18\. Compatibilidad

Compatible con:

* Google Chrome
* Microsoft Edge
* Firefox
* Brave
* Opera

\------------------------------------------------------------------------------------

# 19\. Limitaciones actuales

Actualmente:

* No detecta paredes automáticamente.
* No usa propagación RF avanzada.
* No calcula reflexión.
* No tiene IA de predicción.
* Usa interpolación simplificada.

Aun así, es muy útil para:

* Auditorías WiFi.
* Planificación.
* Visualización rápida.
* Estudios internos.
* Documentación técnica.

\------------------------------------------------------------------------------------

# 20\. Licencia

Uso interno/local.

Puede modificarse libremente según las necesidades de la empresa.

\------------------------------------------------------------------------------------

# 21\. Edición avanzada y simulación de Access Points (actualización)

Se ha añadido un nuevo sistema avanzado de gestión de APs que permite editar y simular configuraciones de red de forma mucho más flexible.

Cambios añadidos:
* Edición completa de APs ya colocados
* Selección de APs directamente desde el mapa
* Visualización y modificación de todas las señales registradas
* Compatibilidad con proyectos importados
* Posibilidad de colocar múltiples APs en la misma posición
* Activación y desactivación individual de APs
* Resaltado visual de APs activos, desactivados y seleccionados
* Nueva interfaz de gestión con botones de editar, activar/desactivar y eliminar
* Compatibilidad con proyectos antiguos
* Recalculo automático del mapa de calor en tiempo real

Resultado:

Ahora es posible crear distintas simulaciones sobre un mismo Access Point, comparar configuraciones y analizar el impacto de cada cambio de forma rápida y visual, todo funcionando completamente en local.

\------------------------------------------------------------------------------------

# 22\. Exportación de datos a Excel (actualización)

Se ha añadido una nueva función de exportación a Excel (.xlsx) para generar automáticamente una hoja con todas las mediciones registradas de los Access Points.

Funcionalidades añadidas:
* Exportación automática de todos los APs a Excel
* Inclusión de todas las mediciones registradas
* Separación de datos de 2.4 GHz y 5 GHz
* Exportación de señales a 5m y 10m en todas las direcciones
* Compatibilidad total con APs activos y desactivados
* Generación local del archivo sin servidores externos
* Datos exportados

Cada fila del Excel incluye:

* Nombre del AP
* Mediciones 2.4 GHz:
* ↑ 5m
* ↓ 5m
* ← 5m
* → 5m
* ↑ 10m
* ↓ 10m
* ← 10m
* → 10m
* Mediciones 5 GHz:
* ↑ 5m
* ↓ 5m
* ← 5m
* → 5m
* ↑ 10m
* ↓ 10m
* ← 10m
* → 10m
  
Resultado:

Ahora la aplicación permite generar documentación técnica y reportes de cobertura WiFi de forma automática, facilitando auditorías, análisis y comparativas externas mediante hojas de cálculo Excel.

\------------------------------------------------------------------------------------

# 23\. Sistema de zoom del mapa (actualización)

Se ha añadido un nuevo sistema de zoom visual para facilitar la navegación y el análisis sobre mapas grandes y planos complejos.

Funcionalidades añadidas:
* Botón de ampliar zoom (+)
* Botón de reducir zoom (-)
* Botón para restaurar zoom al 100%
* Escalado visual únicamente del mapa
* El panel lateral permanece fijo y sin cambios
* Compatible con scroll horizontal y vertical
* No modifica cálculos, distancias ni posiciones reales
* Mejoras visuales
* Mayor precisión al colocar APs
* Navegación más cómoda en mapas grandes
* Mejor visualización de zonas densas
* Facilita el análisis de cobertura y simulaciones
  
Resultado:

* Ahora es posible ampliar o reducir la vista del mapa dinámicamente sin afectar ningún dato técnico del proyecto, mejorando considerablemente la experiencia de uso durante auditorías y simulaciones WiFi.

\------------------------------------------------------------------------------------

# 24\. Sistema de paredes y atenuación de señal (actualización)

Funcionalidades añadidas:

* Herramienta para dibujar paredes directamente sobre el plano
* Selección de distintos materiales de construcción
* Aplicación automática de pérdidas de señal según el material
* Representación visual de paredes mediante colores diferenciados
* Cálculo dinámico de atenuación sobre el mapa de calor
* Compatibilidad con exportación e importación de proyectos JSON
* Materiales soportados
* Cristal
* Pladur
* Ladrillo
* Hormigón
* Metal

Cada material aplica una atenuación distinta en dB para simular el comportamiento real de la señal WiFi al atravesar obstáculos físicos.

Resultado:

* Ahora el sistema genera mapas de cobertura mucho más precisos y realistas, permitiendo simular entornos reales de oficinas, viviendas o naves industriales con obstáculos físicos que afectan directamente a la propagación de la señal inalámbrica.


\------------------------------------------------------------------------------------

# 24-2\. Mejora en el punto de las paredes  (actualización)

Funcionalidades añadidas:

* Botón para ocultar/mostrar menú
* Herramienta para poder eliminar muros y paredes

Resultado:

* Ahora puedes ocultar el menú de herramientas para visualizar de manera más cómoda el contenido. También puedes eliminar muros y paredes en caso de haberte equivocado o querer modificarlo.

\------------------------------------------------------------------------------------

# 24-3\. Mejora en los APs y las paredes  (actualización)

Mover APs/paredes con drag & drop. Funciones añadidas:

APs:

* seleccionar AP
* Arrastrarlo
* Reposicionarlo
* Actualizar heatmap en tiempo real

Paredes:

* Seleccionar pared
* Moverla completa
* Mantener longitud/orientación
* Recalcular atenuación automáticamente
