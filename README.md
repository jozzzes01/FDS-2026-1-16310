# FDS-2026-1-16310 — Análisis de Tendencias de Videos de YouTube (Gran Bretaña)

Proyecto final del curso **Fundamentos de Data Science (1ACC0216)** — Ciclo 2026-1
**Universidad Peruana de Ciencias Aplicadas (UPC)**
**Sección 16310 · Grupo 1 — País asignado: Gran Bretaña (GB)**

---

## Objetivo del proyecto

Aplicar la metodología **CRISP-DM** para analizar las tendencias de los videos de YouTube en Gran Bretaña y generar conocimiento útil para una empresa de marketing digital. El proyecto busca identificar qué categorías y canales dominan las tendencias, cómo evoluciona el volumen de contenido a lo largo del tiempo, qué contenido tiene mejor recepción del público, y evaluar si es factible predecir el número de vistas de un video a partir de sus características.

## Integrantes

- [Nombre 1] — Business Project Sponsor
- [Nombre 2] — Data Engineer
- [Nombre 3] — Data Analyst
- [Nombre 4] — Data Scientist

## Descripción del conjunto de datos

El dataset **Trending YouTube Video Statistics** es un registro diario de los videos de mayor tendencia en YouTube. Para este proyecto se utilizó el archivo correspondiente a Gran Bretaña (`GBvideos.csv`) junto con el archivo de categorías (`GB_category_id.json`).

- **Registros:** 38 916 filas (apariciones de videos en tendencia)
- **Videos únicos:** 3 272
- **Periodo:** 14 de noviembre de 2017 al 14 de junio de 2018
- **Columnas principales:** `video_id`, `trending_date`, `title`, `channel_title`, `category_id`, `publish_time`, `tags`, `views`, `likes`, `dislikes`, `comment_count`, `description`, entre otras.

El documento PDF con la descripción completa del proyecto se encuentra adjunto en este repositorio.

## Estructura del repositorio

```
FDS-2026-1-16310/
├── data/
│   ├── GBvideos.csv.gz         # Dataset inicial comprimido (descomprimir con gunzip)
│   ├── GB_category_id.json     # Categorías de video
│   └── GBvideos_clean.csv.gz   # Dataset final limpio comprimido
├── code/
│   └── upc-2026-01-16310-1-tf.ipynb   # Notebook con el pipeline CRISP-DM
├── README.md
└── upc-2026-01-16310-1-tf.pdf  # Informe final
```

## Metodología

El proyecto sigue las fases de CRISP-DM:

1. **Comprensión del negocio** — Definición de objetivos y variable a predecir (`views`).
2. **Comprensión de los datos** — Recolección, descripción, exploración y verificación de calidad.
3. **Preparación de los datos** — Limpieza, tratamiento de outliers y creación de nuevas variables.
4. **Modelado y evaluación** — Regresión Lineal y Random Forest para predecir las vistas.

## Conclusiones

- **Music** y **Entertainment** dominan las tendencias en GB (más del 58 % del contenido).
- Las categorías que más gustan en promedio son **Nonprofits & Activism** y **Music**; las de menor aceptación relativa son **Travel & Events** y **News & Politics**.
- **Shows** y **Pets & Animals** presentan la mejor proporción Me gusta / No me gusta.
- Los canales más recurrentes en tendencia son programas nocturnos (The Tonight Show, Ellen, Jimmy Kimmel, SNL).
- **Es factible predecir el número de vistas:** el modelo Random Forest alcanzó un R² ≈ 0.99, muy superior a la regresión lineal. Las variables `likes` y `dislikes` son los predictores más influyentes.

### Limitaciones
- El dataset no incluye columnas geográficas (`state`, `lat`, `lon`), por lo que el requerimiento 7 (análisis por Estado) no pudo resolverse.
- El dataset solo contiene la cantidad de comentarios, no su texto, por lo que el requerimiento 8 (comentarios positivos) no pudo resolverse mediante análisis de sentimiento.

## Licencia

Este proyecto se distribuye bajo la licencia **MIT**. Ver el archivo `LICENSE` para más detalles.

El conjunto de datos original proviene de [Kaggle — Trending YouTube Video Statistics](https://www.kaggle.com/datasets/datasnaek/youtube-new).
