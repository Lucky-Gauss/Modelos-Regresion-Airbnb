# Modelos de Regresión Aplicados

Material de apoyo para el artículo sobre el precio de alojamientos de Airbnb en Barcelona y Madrid y para el trabajo de simulación de regresión múltiple. Universidad de Costa Rica, II ciclo de 2026.

**Integrantes:** Anjerson Yamir Zamora Salas, Luis Mario Navarro Garita y Scarleth Vanessa Gómez Hurtado.

## Bases de datos

| Archivo | Uso |
| --- | --- |
| [articulo/Airbnb.RData](articulo/Airbnb.RData) | Base del artículo sobre precios de alojamientos. |
| [simulacion/Airbnb_simulacion.RData](simulacion/Airbnb_simulacion.RData) | Base de referencia utilizada en la simulación. |

Ambas bases contienen 300 observaciones. Debe usarse el archivo que corresponde a cada trabajo, porque tienen estructuras distintas.

## Cómo ejecutar la simulación

1. Abrir R o RStudio con conexión a internet.
2. Copiar únicamente el código de la primera columna del **anexo B del informe final**, respetando el orden de todas las filas.
3. Pegar el código en un script de R y ejecutarlo completo, desde el inicio. Las explicaciones de la segunda columna no forman parte del código.

El anexo instala `car` y `ggplot2` si faltan y descarga la base desde este repositorio. Después ejecuta el ejemplo manual, los siete escenarios principales, la comprobación adicional y los escenarios de las curvas.

Las cuatro figuras se muestran en R y se guardan en la carpeta de trabajo con estos nombres:

- `Figura_1_varianza_Y.png`
- `Figura_2_varianza_u.png`
- `Figura_3_error_tipo_I.png`
- `Figura_A1_tamano.png`

La carpeta de salida puede consultarse con `getwd()`. La ejecución completa ajusta 44 000 modelos y puede tardar varios minutos. Las semillas fijadas permiten reproducir los resultados.

## Cargar solamente una base en R

Estos ejemplos descargan y cargan los datos. Para reproducir el análisis completo se necesita además el código del trabajo correspondiente.

### Base de simulación

```r
url_base <- paste0(
  "https://raw.githubusercontent.com/",
  "Lucky-Gauss/Modelos-Regresion-Airbnb/",
  "main/simulacion/Airbnb_simulacion.RData"
)
archivo <- tempfile(fileext = ".RData")
download.file(url_base, archivo, mode = "wb")
objetos <- load(archivo)
unlink(archivo)
objetos
```

### Base del artículo

Ejecutar este bloque en una sesión nueva si antes se cargó la base de simulación, para evitar reemplazar objetos con el mismo nombre.

```r
url_base <- paste0(
  "https://raw.githubusercontent.com/",
  "Lucky-Gauss/Modelos-Regresion-Airbnb/",
  "main/articulo/Airbnb.RData"
)
archivo <- tempfile(fileext = ".RData")
download.file(url_base, archivo, mode = "wb")
objetos <- load(archivo)
unlink(archivo)
objetos
```

## Verificación

El 18 de noviembre de 2026 se comprobó que ambos archivos públicos se descargan y son idénticos a sus originales.

El código extraído del anexo B de simulación se ejecutó en R 4.3.3 con la base descargada desde GitHub. Reprodujo los coeficientes del ejemplo, los siete escenarios principales, la comprobación adicional y los datos de las cuatro figuras del informe.

Para conservar los enlaces usados en los trabajos, deben mantenerse los nombres y las rutas de las bases en la rama `main`.
