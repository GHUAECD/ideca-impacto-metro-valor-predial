# IDECA - Análisis del impacto del Metro sobre el valor predial

## Descripción

Proyecto de análisis de variables prediales y territoriales asociadas al avalúo catastral 2026 en el corredor piloto de la Primera Línea del Metro de Bogotá, entre las estaciones Calle 63-15 y Calle 72-16. La memoria técnica describe un ámbito de 16.613 lotes en 46 barrios; los conteos varían entre la consolidación, preparación y muestra efectiva de modelado.

El estudio integra características catastrales, construcción, propiedad horizontal y accesibilidad a infraestructura y equipamientos para examinar cómo varía espacialmente la asociación entre proximidad al Metro y valor predial. La memoria también plantea un contraste con ofertas de venta y arriendo; ese componente no está reproducido por los tres notebooks entregados.

Es un análisis transversal del avalúo, no una comparación antes/después ni una identificación causal del efecto de la obra. El avalúo catastral y el precio de oferta son medidas distintas. El término «impacto» del título debe leerse dentro de ese alcance estadístico.

La fuente principal de contexto y metodología es la [memoria técnica](1%20-%20Documentaci%C3%B3n/Memoria_tecnica_modelo_valor.docx), contrastada con el código y las salidas existentes. Esta documentación se elaboró mediante inspección de solo lectura, sin ejecutar notebooks ni recalcular modelos.

**Estado de reproducción y publicación:** faltan insumos auxiliares y hay discrepancias entre versiones. Las fuentes y CSV quedan excluidos de Git, pero los notebooks originales conservan salidas con identificadores prediales y rutas de trabajo. Deben revisarse antes de una publicación pública; `.gitignore` no oculta sus contenidos incrustados. No se modificaron esos originales.

## Distribuci?n de datos y archivos pesados

El repositorio p?blico contiene principalmente c?digo, metodolog?a, documentaci?n e instrucciones de reproducci?n. Las fuentes pesadas y los resultados tabulares se conservan ?nicamente en el entorno local: no se distribuyen mediante GitHub, Git normal ni Git LFS. No se comprimen nuevamente, dividen, mueven ni eliminan para incorporarlos al repositorio.

El usuario debe proporcionar u obtener los archivos de entrada mediante las fuentes institucionales correspondientes y con los permisos aplicables. Las salidas CSV/XLSX de gran tama?o se generan localmente al ejecutar el proyecto en un entorno autorizado. No hay enlaces de descarga confirmados para el conjunto completo de datos y no se ofrece su descarga desde este repositorio.

Inventario local de archivos superiores a 100 MB (MB decimales):

| Archivo | Tama?o | Estado |
| --- | ---: | --- |
| `2 - Fuentes/bd_uaecd_2026.gdb-20260810T154558Z-1-001.zip` | 983,19 MB | Ignorado, no rastreado |
| `2 - Fuentes/Predio-20260810T154644Z-1-001.zip` | 392,39 MB | Ignorado, no rastreado |
| `2 - Fuentes/Zona_piloto_GD.gpkg` | 220,77 MB | Ignorado, no rastreado |
| `4 - Salidas/dataset_final_predios_completo.csv` | 136,50 MB | Ignorado, no rastreado |

Tambi?n se excluyen el ZIP `BaseDatosGD` (34,79 MB) y el CSV `dataset_modelo_lote_umbral100.csv` (6,98 MB): la restricci?n de distribuci?n no depende solamente del tama?o. `.gitignore` aplica patrones de ruta y nombre, no umbrales de tama?o; cualquier nuevo formato de datos requiere comprobar su exclusi?n antes de publicarlo.

### Revisi?n de archivos candidatos a publicaci?n

- **Memoria t?cnica (5,07 MB):** contiene nombres y atribuciones de personas del equipo, adem?s del contacto institucional. No se detectaron rutas locales sensibles ni patrones evidentes de credenciales en el texto XML inspeccionado, ni objetos adjuntos en `word/embeddings`. Los nombres del equipo requieren revisi?n institucional de su difusi?n; no se certifica ausencia absoluta de informaci?n sensible en las im?genes del documento.
- **Consignaci?n (1,10 MB):** contiene 34 objetos de salida, aproximadamente 1,03 MB serializados, con tablas, imagen y datos prediales guardados.
- **Manipulaci?n (0,03 MB):** contiene cinco objetos de salida, aproximadamente 0,002 MB serializados, incluidos identificadores de lotes.
- **Modelos (12,95 MB):** contiene 83 objetos de salida, aproximadamente 12,78 MB serializados, con tablas, im?genes y HTML interactivo con atributos por lote. No debe considerarse un archivo de c?digo sin datos incrustados.
- **JPG GWR (0,13 MB):** no muestra identificadores personales ni valores prediales individuales visibles; conserva la evaluaci?n de publicaci?n descrita en Resultados.

**Recomendaci?n antes de publicaci?n: limpiar outputs del notebook.** Aplica a los tres notebooks. Tambi?n deben revisarse las rutas de Drive en las celdas fuente: limpiar outputs no elimina esas rutas. No se detectaron patrones evidentes de tokens o claves privadas en el examen realizado, pero no constituye una auditor?a exhaustiva de secretos. No se modificaron notebooks, memoria ni imagen.

En la revisi?n complementaria, Git rastrea los seis archivos de documentaci?n/configuraci?n, `LICENSE`, la memoria, los tres notebooks y el JPG; salvo `LICENSE`, aparecen como incorporaciones preparadas en el ?ndice. Ning?n archivo mayor de 100 MB est? rastreado. Esta revisi?n no modific? el ?ndice ni cre? commits.

## Objetivo

Examinar la relación entre la proximidad a la Línea 1 del Metro y el avalúo catastral 2026 en el corredor piloto, determinando si esa asociación es homogénea o varía según la ubicación. El objetivo de la memoria se operacionaliza mediante consolidación predial, diagnóstico de dependencia espacial, comparación de modelos globales y locales, y análisis territorial y socioeconómico de los coeficientes estimados.

## Estructura

Árbol local de la entrega; los archivos de datos permanecen en disco aunque se excluyan del repositorio público:

```text
ideca-impacto-metro-valor-predial/
├── README.md
├── requirements.txt
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── 1 - Documentación/
│   └── Memoria_tecnica_modelo_valor.docx
├── 2 - Fuentes/
│   ├── README.md
│   ├── BaseDatosGD.gdb-20260810T154550Z-1-001.zip
│   ├── bd_uaecd_2026.gdb-20260810T154558Z-1-001.zip
│   ├── Predio-20260810T154644Z-1-001.zip
│   └── Zona_piloto_GD.gpkg
├── 3 - Código/
│   ├── Consignacion_base_de_datos.ipynb
│   ├── Manipulacion_datos_pre_modelo.ipynb
│   └── Modelos_de_valor.ipynb
└── 4 - Salidas/
    ├── README.md
    ├── dataset_final_predios_completo.csv
    ├── dataset_modelo_lote_umbral100.csv
    └── Mapa de calor de coeficientes GWR.jpg
```

## Metodología

1. **Integración predial.** Construcción de la llave de lote `barmanpre`, integración de `Predios_GD`, `Predio` y `Calificacion` por lote y CHIP, selección de la calificación más reciente y del uso con mayor área, y asociación con geometría y variables de `LoteData`.
2. **Depuración y accesibilidad.** Exclusión de vías, servidumbres y espacio público que no intersecta parques; geometrías 2D y centroides en `EPSG:6247`. Distancias Manhattan a estaciones de Metro, TransMilenio, salud y educación; distancias geométricas euclidianas al trazado del viaducto y polígonos de parques. Clasificación por isócronas suministradas como fuente independiente.
3. **Preparación por lote.** Filtrado de avalúo y área de terreno inválidos, transformación `log(1 + distancia)`, destino y uso por moda del lote, agrupación de destinos con frecuencia menor a 100 y descarte de dummies con menos de 10 lotes. Se promedian avalúo y área construida, se conservan primeros valores de atributos compartidos y se clasifica PH con proporción mayor o igual a 0,5.
4. **Especificación del modelo.** El notebook de modelos multiplica esos promedios por `n_chips_por_lote` para construir sumas y define `TARGET = log_valor_sum`. Filtra valores no finitos. La transformación se aplica a todos los lotes, aunque los comentarios la describan en términos de PH. La interpretación económica exige verificar la granularidad original de `LoteData`.
5. **Estimación y evaluación.** OLS, VIF, Moran global y pruebas LM; modelos SEM, SAR y SARAR con una matriz de 10 vecinos, distancia inversa y normalización por fila. GWR con predictores estandarizados y kernel bisquare; XGBoost con validación cruzada aleatoria de cinco particiones.
6. **Lectura territorial.** Mapas de coeficientes, análisis por estación, estrato, destino, bandas y sector catastral, pruebas de sensibilidad y resumen GWR por banda. Estos productos describen asociaciones condicionadas al modelo.

## Flujo de ejecución

El orden se confirma por las lecturas y exportaciones del código, no solo por los nombres:

| Orden | Notebook | Función y transferencia de datos |
| --- | --- | --- |
| 1 | [Consignacion_base_de_datos.ipynb](3%20-%20C%C3%B3digo/Consignacion_base_de_datos.ipynb) | Consolida información por chip/predio, construye accesibilidad y exporta `dataset_final_predios_completo.csv`. También prevé XLSX y dos tablas de apoyo para ofertas. |
| 2 | [Manipulacion_datos_pre_modelo.ipynb](3%20-%20C%C3%B3digo/Manipulacion_datos_pre_modelo.ipynb) | Lee el CSV anterior, depura y agrega por lote, codifica variables y exporta `dataset_ingenieria_caracteristicas.csv`. |
| 3 | [Modelos_de_valor.ipynb](3%20-%20C%C3%B3digo/Modelos_de_valor.ipynb) | Lee `dataset_ingenieria_caracteristicas.csv`, define la variable objetivo sumada, estima modelos, evalúa residuos y genera análisis y visualizaciones territoriales. |

El archivo `dataset_ingenieria_caracteristicas.csv` no está en la entrega. El CSV presente `dataset_modelo_lote_umbral100.csv` tiene un esquema compatible con preparación por lote, pero no hay una exportación con ese nombre en el código actual. No debe renombrarse ni asumirse equivalente sin verificar su procedencia.

## Fuentes de información

| Fuente | Aporte al flujo confirmado |
| --- | --- |
| `BaseDatosGD.gdb`, dentro de su ZIP | Universo piloto (`Predios_GD`), geometría (`Lote`), áreas y avalúo 2026 (`LoteData`), estaciones y trazado de Línea 1. |
| `bd_uaecd_2026.gdb`, dentro de su ZIP | `Predio` y `Calificacion`: atributos catastrales, destino, uso, estrato, PH y relaciones entre predios y lotes. |
| ZIP `Predio` | Incluye `Estación_troncal`, `LOTE`, `ZonaPiloto15Min` y `PREDIO.dbf`. La lectura de TransMilenio necesita el shapefile habilitado fuera del ZIP. |
| `Zona_piloto_GD.gpkg` | Capas de parques, colegios e IES empleadas para accesibilidad, además de otras capas de contexto. |
| Shapefiles adicionales | `Isócronas.shp`, `salida.shp` de IPS corregidas y `SECTOR.shp` son referenciados, pero no se encontraron en la entrega. |

La memoria identifica fuentes internas del proyecto y capas de datos abiertos Bogotá. No proporciona en el flujo inspeccionado enlaces inequívocos de descarga para todos los insumos; no se asignan URLs por inferencia. Tampoco se identificó una fuente inequívoca de ofertas de venta/arriendo.

Para reproducir el análisis, un usuario debe disponer de las GDB, el GeoPackage, los shapefiles completos y sus permisos de uso, además del CSV intermedio generado por cada etapa. Consulte el [inventario de fuentes](2%20-%20Fuentes/README.md), que distingue contenido confirmado de archivos faltantes y describe su organización.

## Variables

| Categoría | Variables o transformaciones principales |
| --- | --- |
| Valor y construcción | `valor_avaluo_2026`, áreas de terreno y construida; promedios por lote en preparación y sumas reconstruidas en modelado. Objetivo principal: `log_valor_sum`. El valor por m² se deriva en preparación, pero no es el objetivo principal. |
| Clasificación predial | Destino económico, uso, estrato y propiedad horizontal. El modelo global utiliza `ph_bin` y dummies `dest_*`; el estrato se usa en análisis posteriores, no como regresor final. |
| Ubicación | Centroides `cx`, `cy`, geometría y sector catastral; llaves prediales para integración, no para divulgación de registros. |
| Infraestructura y equipamientos | Logaritmos de uno más la distancia a Metro, viaducto, TransMilenio, parques, salud y educación. |
| Variables exploratorias | Estación cercana, bandas de isócrona, dummies de uso y estación de referencia. `uso_*`, `iso_*` y `est_iso_*` se excluyen del modelo global principal. |

GWR usa nueve predictores: áreas, seis distancias y PH. No incluye las dummies de destino ni `cx`/`cy` como regresores; las coordenadas definen la ponderación geográfica. Su especificación no es idéntica a la de los modelos globales.

## Modelos

Los seis modelos siguientes tienen instrucciones de ajuste en `Modelos_de_valor.ipynb`. Comparten como objetivo `log_valor_sum`, el logaritmo de la suma reconstruida de avalúo por lote.

| Modelo | Propósito y resultados |
| --- | --- |
| OLS (`statsmodels.OLS`; `spreg.OLS` para diagnóstico) | Línea base lineal; coeficientes globales, ajuste y residuos. Permite diagnosticar multicolinealidad y dependencia espacial con VIF, Moran y LM. |
| SEM (`spreg.GM_Error`) | Modela dependencia espacial en el error; coeficientes, parámetro espacial, pseudo-R² y residuos. |
| SAR (`spreg.GM_Lag`) | Incorpora rezago espacial de la variable dependiente; coeficientes, parámetro autorregresivo, pseudo-R² y residuos. |
| SARAR (`spreg.GM_Combo`) | Combina rezago espacial y error espacial; coeficientes y parámetros para ambos mecanismos. |
| GWR (`mgwr.GWR`) | Estima coeficientes que varían por localización; produce coeficientes locales, R² local, AICc, residuos y mapas. El código selecciona explícitamente `bw=750`, `kernel='bisquare'`, `fixed=False`. |
| XGBoost (`XGBRegressor`) | Contraste predictivo no lineal con las variables del modelo global: 500 árboles, profundidad 6 y semilla 42. Produce RMSE/R² en validación cruzada de cinco particiones y métricas separadas del ajuste sobre toda la muestra. |

Con `fixed=False`, GWR utiliza un vecindario adaptativo: `bw=750` representa vecinos, no una distancia fija de 750 metros. Esta lectura se confirmó en la [documentación oficial de mgwr](https://mgwr.readthedocs.io/en/latest/generated/mgwr.gwr.GWR.html) y difiere de la memoria y algunos comentarios.

SHAP está importado y descrito en la memoria, pero no se encontraron llamadas que calculen valores SHAP. Los clústeres LISA y el modelado independiente de ofertas también se mencionan en la memoria, sin implementación identificada en los notebooks entregados. No se presentan como componentes ejecutables disponibles.

## Instalación

El entorno de desarrollo documentado es Google Colab. Los tres notebooks importan `google.colab.drive` y montan Drive; la instalación de paquetes por sí sola no los convierte en notebooks locales portables. No se entregó un archivo de versiones del entorno; un metadato del notebook de modelos indica Python 3.10.0, lo que no prueba compatibilidad de todas las dependencias con una versión concreta.

`requirements.txt` recoge los paquetes externos importados y `openpyxl`, solicitado explícitamente por la exportación XLSX. Incluye `shap` porque su importación forma parte del código, aunque no haya un análisis SHAP implementado. No incluye módulos de la biblioteca estándar (`gc`, `re`, `unicodedata`, `warnings`, `time`, `subprocess`, `glob`, `os`) ni `google.colab`, suministrado por Colab.

Para preparar un entorno local de revisión, desde la raíz del repositorio en PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

Si necesita una interfaz local para abrir copias de los notebooks, instale JupyterLab por separado; es una herramienta de ejecución, no un import del proyecto:

```powershell
.\.venv\Scripts\python.exe -m pip install jupyterlab
.\.venv\Scripts\python.exe -m jupyter lab
```

En un entorno Colab autorizado, ponga `requirements.txt` en el directorio de trabajo y ejecute `%pip install -r requirements.txt` en una celda de preparación independiente. Se requiere soporte de lectura FileGDB, GeoPackage y shapefile en los controladores geoespaciales. La instalación y la ejecución no se realizaron durante esta revisión.

## Ejecución

1. Prepare un entorno de trabajo separado con copias de los notebooks y fuentes autorizadas. Preserve los originales y las salidas entregadas.
2. Complete los insumos faltantes descritos en la guía de fuentes. Verifique nombres de capas, campos y CRS antes del cálculo.
3. Prepare las ubicaciones esperadas por las rutas de Drive o ajuste las rutas únicamente en las copias de trabajo. Configure exportaciones en una ubicación nueva. Los notebooks originales no usan automáticamente las carpetas del repositorio.
4. Ejecute las celdas de consignación en orden. Su CSV principal se escribe con una ruta relativa al directorio de ejecución; asegure que la preparación lea ese archivo recién producido, sin reemplazar el original.
5. Ejecute la preparación en orden y compruebe el intermedio `dataset_ingenieria_caracteristicas.csv`. Registre esquema, conteos y parámetros antes del modelado.
6. Ejecute modelos desde un kernel limpio, respetando el orden de celdas: varios análisis dependen de objetos creados antes en ese mismo notebook. Entre notebooks, la transferencia identificada es por CSV, no por variables compartidas en memoria.
7. Registre versiones, fuentes, parámetros, semillas, exclusiones y métricas. Compare contra la memoria y las salidas guardadas, sin dar por supuesto que corresponden a la misma corrida.

Estos pasos describen el flujo previsto. La entrega actual no permite garantizar una ejecución completa sin resolver las observaciones siguientes; no se reentrenaron modelos ni se sobrescribieron resultados para esta documentación.

## Resultados

La entrega contiene una base consolidada por predio/chip, una tabla preparada por lote y un JPG de coeficientes GWR. El código también prevé un XLSX, tablas de apoyo a ofertas, un resumen GWR por banda y gráficos dentro de los notebooks. El [inventario de salidas](4%20-%20Salidas/README.md) documenta productores, archivos ausentes y límites de trazabilidad.

La memoria interpreta heterogeneidad espacial de la asociación con el Metro entre ambas estaciones. Las métricas guardadas en el notebook pertenecen a una especificación o ejecución que no coincide plenamente con las cifras de la memoria:

| Indicador | Memoria técnica, resultados | Salida guardada del notebook |
| --- | --- | --- |
| Moran I residual OLS | 0,2981 | 0,4289 |
| Ajuste SAR (R² en memoria; pseudo-R² en código) | 0,8428 | 0,8969 |
| Moran I residual SAR | 0,1072 | 0,3460 |
| Moran I residual GWR | 0,0904 | 0,1316 |
| XGBoost, R² de validación cruzada | 0,9569 | 0,9642 |
| XGBoost, RMSE de validación cruzada | 0,2167 | 0,2095 |

Son resultados documentados o almacenados, no métricas recalculadas por esta revisión. No se atribuye la diferencia a una causa específica sin un registro de versiones y ejecución.

El [JPG GWR](4%20-%20Salidas/Mapa%20de%20calor%20de%20coeficientes%20GWR.jpg) muestra el coeficiente local de distancia a estación. No contiene identificadores ni avalúos individuales visibles y resulta razonable como ilustración técnica sujeta a revisión institucional del detalle espacial. Se recomienda acompañarlo de una leyenda explícita: en esta imagen rojo indica coeficiente negativo y verde positivo; no representa valorización causal ni porcentajes directamente. No existe en el notebook una exportación que permita certificar la corrida exacta que produjo ese JPG.

## Limitaciones

- El corte transversal del avalúo 2026 no permite aislar causalmente el efecto de la obra, del anuncio o de la operación futura del Metro. Los resultados no se extrapolan automáticamente al resto de Bogotá.
- La agregación por lote, la mezcla de destinos y la escala de áreas/avalúos pueden modificar la interpretación. El primer notebook replica atributos de `LoteData` en los chips del lote y el tercero multiplica promedios por el número de chips: debe confirmarse si los valores de origen ya eran totales de lote para evitar interpretar una posible multiplicación como suma de unidades independientes.
- La exclusión de datos no finitos y de áreas construidas no positivas afecta la muestra. La memoria señala una dummy de «Urbanizado No Edificado» constante y problemas de condicionamiento; no se validaron nuevamente las matrices.
- Las distancias Manhattan y euclidianas son aproximaciones geométricas, no recorridos de red ni tiempos de viaje calculados por el pipeline. La clasificación de isócronas presenta una inconsistencia pendiente.
- Persisten residuos espacialmente correlacionados. El notebook advierte inestabilidad local GWR en un grupo pequeño del estrato 2; no debe interpretarse cada extremo como hallazgo sustantivo.
- Las categorías «accesibilidad», «neutro» y «disamenidad» se construyen con percentiles 25/75, no con pruebas de significancia ni exclusivamente con el signo. Los predictores GWR están estandarizados: sus coeficientes no son elasticidades porcentuales directas.
- La validación XGBoost usa particiones aleatorias, no bloques espaciales. Su RMSE de validación se compara con residuos SAR dentro de muestra; no es una comparación equivalente de desempeño fuera de muestra ni una validación causal.
- Faltan fuentes y trazabilidad de ejecución. No se documenta un despliegue operativo; el producto entregado es el conjunto de notebooks, memoria y resultados.

## Licencia

El archivo [LICENSE](LICENSE) contiene **Apache License 2.0** y se conserva sin modificaciones. La memoria técnica declara **Creative Commons Attribution 4.0 International (CC BY 4.0)**. Esta diferencia queda pendiente de aclaración institucional sobre el alcance por artefacto. No se presume que la licencia del repositorio autorice redistribuir las fuentes institucionales ni todos los resultados.

## Entidad

Unidad Administrativa Especial de Catastro Distrital - UAECD  
Infraestructura de Datos Espaciales para el Distrito Capital - IDECA

## Observaciones para mejorar la reproducibilidad

Los números de celda siguientes cuentan desde 1 e incluyen celdas Markdown. Se reportan hallazgos sin corregir los notebooks ni la memoria.

1. **Rutas y entorno.** Los tres notebooks contienen rutas absolutas de Colab/Google Drive vinculadas a la organización del autor. No se encontraron rutas OneDrive ni rutas Windows de usuario en sus celdas fuente. No se reproducen las rutas institucionales en esta documentación. El montaje de Drive y algunas instalaciones dinámicas impiden una ejecución local directa.
2. **Insumos faltantes.** No se encontraron `Isócronas.shp`, `salida.shp` ni `SECTOR.shp`. TransMilenio sí está en el ZIP `Predio`, pero los notebooks esperan un shapefile accesible directamente. No se han extraído los ZIP.
3. **Nombre del intermedio.** Preparación exporta `dataset_ingenieria_caracteristicas.csv` (celda 15) y modelos lo lee (celda 6). La entrega solo contiene `dataset_modelo_lote_umbral100.csv`; no hay evidencia suficiente para certificarlo como sustituto de esa versión.
4. **Isócronas.** Consignación, celda 32, usa nombres `Calle 63`/`Calle 72`; el bloque de apoyo a ofertas usa `Calle 63-15`/`Calle 72-16`. La comparación con `estacion_metro_cercana` puede no coincidir en el primer bloque. El CSV consolidado inspeccionado tiene sus 103.110 filas en `>1200`, mientras el CSV preparado conserva columnas de otras bandas. Se requiere verificar consistencia entre fuentes y versiones.
5. **Nombres de capas y CRS.** El GeoPackage registra `Colegios122025` y el código solicita `colegios122025`. En modelos, las capas de Metro se cargan y se inspeccionan, pero el bloque titulado reproyección no ejecuta `to_crs` antes de superponer los mapas estáticos. La capa de sectores sin CRS recibe uno supuesto. Estas condiciones requieren validación en la fuente concreta.
6. **GWR fijo frente a adaptativo.** La memoria y comentarios describen 750 metros; las celdas 47 y 49 usan `fixed=False`, vecindario adaptativo de 750 vecinos. La elección de 750 está escrita explícitamente después del barrido, no seleccionada automáticamente por un optimizador.
7. **Variables y agregación.** Preparación promedia avalúo/área construida; modelos reconstruye sumas y usa `log_valor_sum`. La memoria y algunos textos conservan referencias al promedio, al estrato como control y a `log(1 + área construida)`, mientras el modelo final excluye estrato y usa el logaritmo de área sumada positiva. GWR excluye además destino y coordenadas como regresores. Debe verificarse la granularidad de `LoteData` antes de interpretar las sumas.
8. **Análisis documentados no disponibles.** SHAP solo se importa; no hay cálculo SHAP ni LISA, notebook de ofertas o base inequívoca de venta/arriendo identificados. Tampoco se encontró la comparación ejecutable de umbrales 100/30, la prueba F de agregación ni la comparación GWR con/sin distancias al Metro descritas en la memoria.
9. **Métricas y criterios.** Las cifras de la memoria difieren de las salidas guardadas, como muestra la tabla de resultados. La comparación SEM/SAR/SARAR del código usa pseudo-R², Moran y RMSE; no calcula el AIC que menciona la memoria para esa comparación. AICc sí se calcula en GWR.
10. **Sensibilidad espacial.** La prueba que excluye el 1 % superior por número de chips reconstruye KNN normalizado por fila sin reponer los pesos de distancia inversa ni el tratamiento de duplicados del modelo principal. Cambia más que la muestra; no aísla exclusivamente la influencia de esos lotes.
11. **Estado de ejecución.** Los objetos `mask`, `W_final`, `coef_df`, `df_modelo_mask` y las capas cartográficas dependen de celdas previas. No se identificó dependencia directa de variables en memoria de otro notebook. Las salidas almacenadas no acreditan una corrida limpia del código actual; no se ejecutó para comprobarlo.
12. **Detalles de diagnóstico.** El último resumen de preparación busca `dest_*` en `df`, la tabla de entrada, y no en `gdf_lote`, por lo que puede mostrar un diagnóstico vacío. La conversión de estrato a entero en modelos puede fallar con nulos, pues estrato no forma parte del filtro principal de finitud. Algunas visualizaciones exigen coeficientes a ambos lados de cero. Se reportan como condiciones a revisar, sin modificaciones.
13. **Textos desactualizados.** Un Markdown describe descarga web de sectores, pero el código busca `SECTOR.shp` local. Algunos encabezados anuncian Folium aunque las figuras siguientes usan Matplotlib. El «estrato dominante» por barrio se calcula como media redondeada, no como moda. La columna GWR rotulada `std err` resume dispersión espacial de coeficientes, no errores estándar de estimación.
14. **Dependencias y aleatoriedad.** No hay versiones fijadas; `requirements.txt` documenta imports y motor XLSX. Hay semillas explícitas para jitter y XGBoost, pero las permutaciones de Moran no tienen una semilla propia fijada en cada llamada. El consumo de memoria depende de las GDB, matrices de distancia y ajuste GWR.
15. **Publicación.** Git solo rastreaba `LICENSE` durante la revisión; ninguna fuente ni CSV estaba rastreado. Se añadieron exclusiones sin retirar archivos del índice. Los tres notebooks conservan salidas con identificadores prediales; el último gráfico Plotly también incorpora atributos por lote. No deben publicarse tal como están sin revisión de esos contenidos. El JPG no presenta identificadores visibles y no se excluyó automáticamente.
16. **Licencias y trazabilidad.** Apache-2.0 en `LICENSE` y CC BY 4.0 en la memoria requieren delimitar su alcance. No se ha cambiado ninguna licencia ni se ha certificado la autorización de difusión de datos. Tampoco hay una exportación JPG identificable que vincule la imagen con una corrida concreta.
