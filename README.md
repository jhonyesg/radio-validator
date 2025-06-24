# Validador de Enlaces de Streaming de Radios

Este proyecto es una aplicación de escritorio en Python que permite validar enlaces de streaming de radios a partir de archivos de configuración `.ini` o archivos `.csv`. Proporciona una interfaz gráfica intuitiva para importar, filtrar, validar, escuchar y exportar resultados de enlaces de streaming.

---

## Características principales

- **Validación automática de enlaces de streaming** usando `requests`, `ffprobe` y `ffmpeg`.
- **Interfaz gráfica amigable** desarrollada con `tkinter` y `ttkthemes`.
- **Reproducción de streams** directamente desde la aplicación usando VLC.
- **Importación de archivos `.ini` y `.csv`** para cargar listas de radios.
- **Filtrado y búsqueda** de radios en tiempo real.
- **Exportación de resultados a Excel** con formato visual para enlaces operativos y caídos.
- **Copia rápida de enlaces** al portapapeles.
- **Control de volumen y reproducción** integrado.
- **Barra de progreso y estado** para seguimiento de la validación.
- **Soporte para múltiples plataformas** (Windows recomendado).

---

## Estructura del proyecto

```
radio-validator/
├── radios_part1.ini
├── src/
│   └── validador Radios V3.py
├── requirements.txt
└── README.md
```

- `radios_part1.ini`: Archivo de configuración de ejemplo con las radios a validar.
- `src/validador Radios V3.py`: Código fuente principal de la aplicación.
- `requirements.txt`: Lista de dependencias de Python.
- `README.md`: Este archivo.

---

## Requisitos

- **Python 3.8 o superior**
- **ffmpeg** y **ffprobe** instalados y accesibles desde la línea de comandos.
- **VLC Media Player** instalado (para reproducción de streams).
- Sistema operativo: Windows (recomendado por rutas y dependencias).

### Instalación de dependencias Python

Instala las dependencias con:

```sh
pip install -r requirements.txt
```

### Instalación de ffmpeg y VLC

- Descarga e instala [ffmpeg](https://ffmpeg.org/download.html) y asegúrate de agregarlo al PATH.
- Descarga e instala [VLC Media Player](https://www.videolan.org/vlc/).

---

## Uso

1. **Clona o descarga este repositorio.**
2. **Coloca tu archivo `.ini` de radios en la raíz del proyecto** (o usa el de ejemplo).
3. **Ejecuta la aplicación:**

   ```sh
   python src/validador\ Radios\ V3.py
   ```

4. **Selecciona el archivo de configuración** desde el menú desplegable o usa el botón "Seleccionar".
5. **Opcional:** Importa un archivo `.csv` si lo prefieres.
6. **Filtra o busca radios** usando el campo de filtro.
7. **Haz clic en "Realizar Acción"** para validar los enlaces o exportar a Excel.
8. **Reproduce cualquier stream** seleccionando una fila y usando el botón "Reproducir".
9. **Copia enlaces** usando el botón correspondiente.

---

## Formato de archivos de configuración

### Archivo `.ini` (ejemplo)

```ini
[Nombre_Radio]
stream_url = https://ejemplo.com/stream
output_dir = C:\Ruta\de\salida\
log_dir = C:\Ruta\de\logs\
media_name = Nombre_Radio
duration = 1260
start_time = 0
time_ranges = 3-24
acodec = copy
```

Cada sección representa una radio. El campo `stream_url` es obligatorio.

### Archivo `.csv` (ejemplo)

Debe tener al menos las siguientes columnas: `source`, `target`, `status`, `type`, `hits`, `title`.

---

## Explicación técnica del código

- **Interfaz gráfica:** Se usa `tkinter` y `ttkthemes` para una UI moderna y funcional.
- **Carga de archivos:** Permite seleccionar archivos `.ini` o `.csv` desde la interfaz.
- **Validación de enlaces:**  
  - Primero intenta validar con una petición HTTP (`requests.head`).
  - Si falla, usa `ffprobe` para analizar el stream.
  - Si aún falla, intenta descargar unos segundos con `ffmpeg`.
  - El resultado se muestra en la tabla con colores (verde para operativo, rojo para caído).
- **Reproducción:** Usa la librería `python-vlc` para reproducir el stream seleccionado.
- **Exportación:** Los resultados pueden exportarse a Excel con formato visual.
- **Multihilo:** La validación se ejecuta en un hilo separado para no bloquear la interfaz.
- **Control de volumen:** Permite ajustar el volumen del reproductor VLC desde la app.
- **Copia de enlaces:** Permite copiar rápidamente el enlace de streaming al portapapeles.

---

## Dependencias Python

Incluye en tu `requirements.txt`:

```
pandas
openpyxl
requests
python-vlc
pyperclip
ttkthemes
```

---

## Personalización

- Puedes modificar el archivo `.ini` para agregar o quitar radios.
- El código es fácilmente extensible para soportar otros formatos o validaciones adicionales.

---

## Problemas comunes

- **ffmpeg/ffprobe no encontrados:** Asegúrate de que estén en el PATH del sistema.
- **VLC no instalado:** Instala VLC y asegúrate de que la versión de `python-vlc` sea compatible.
- **Errores de permisos:** Ejecuta la aplicación con permisos adecuados si accedes a rutas protegidas.

---

## Licencia

MIT License.

---

## Autor

Desarrollado por Efrain Suarez.

---

## Galería de la Aplicación

### 1. Interfaz del programa vacía

![Interfaz del programa vacía](img/01%20Interfaz%20del%20programa%20Vacio.png)

---

### 2. Validación del archivo INI

![Validación del archivo INI](img/02%20Interfaz%20haciendo%20validacion%20del%20archivo%20%20ini.png)

---

### 3. Aviso de validación de enlaces completada

![Validación completada](img/03%20interfaz%20con%20aviso%20de%20validacio%20de%20enlaces%20completada.png)

---

### 4. Exportación de validación de enlaces a Excel

![Exportación a Excel](img/04%20exportacion%20de%20validacion%20de%20enlaces%20a%20un%20excel.png)

---

### 5. Importación de CSV para validación

![Importación de CSV](img/05%20Importacion%20de%20CVS%20para%20validacion%20.png)

---

¿Tienes dudas o sugerencias? ¡Abre un issue o contribuye al proyecto!