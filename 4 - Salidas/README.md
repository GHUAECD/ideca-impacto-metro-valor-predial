# Resultados y archivos intermedios

Los CSV son datos analíticos de trabajo, no tablas para publicación automática. Se excluyen del control de versiones mediante `.gitignore`; al momento de esta revisión ninguno estaba rastreado por Git. No se copiaron registros individuales a la documentación.

## Archivos presentes

| Archivo | Contenido conceptual y procedencia |
| --- | --- |
| `dataset_final_predios_completo.csv` | Base integrada a nivel chip/predio, con atributos catastrales, identificadores, direcciones, geometría WKT, centroides, áreas, avalúo y accesibilidad. La exportación está implementada en `Consignacion_base_de_datos.ipynb`, celda 50 contando desde 1. El archivo presente contiene 103.110 filas y 16.625 lotes distintos. |
| `dataset_modelo_lote_umbral100.csv` | Tabla a nivel lote con 16.613 filas y lotes distintos, áreas, avalúo, distancias logarítmicas, dummies de destino/uso/isócrona, PH y número de chips. Su esquema es compatible con la etapa de preparación, pero ningún notebook actual exporta ese nombre. No se puede certificar la versión productora ni su equivalencia con el intermedio esperado. |
| `Mapa de calor de coeficientes GWR.jpg` | Distribución espacial del coeficiente local de `log_dist_estacion_metro_m`. Es coherente conceptualmente con los mapas de `Modelos_de_valor.ipynb`, pero no existe una instrucción que guarde ese nombre de JPG: la procedencia exacta de la exportación no está registrada. |

Los tamaños de muestra pertenecen a etapas distintas. En las salidas guardadas de XGBoost se reportan 16.599 observaciones después del filtrado; no se volvió a ejecutar el análisis para verificar la continuidad entre versiones.

## Salidas previstas por el código, no presentes en esta carpeta

| Productor | Archivo o resultado |
| --- | --- |
| Consignación | `dataset_final_predios_completo.xlsx`, copia tabular mediante `openpyxl`; `lookup_chip_isocrona.csv` y `lookup_chip_ph.csv`, tablas de apoyo al análisis de ofertas. |
| Manipulación | `dataset_ingenieria_caracteristicas.csv`, salida efectiva con umbral 100 y mínimo de 10 lotes para dummies; es la entrada que lee el notebook de modelos. |
| Modelos | `gwr_efecto_por_banda.csv`, resumen del coeficiente local por banda, con media, mediana y conteo. También produce tablas de ajuste, diagnósticos, coeficientes, gráficos estáticos y un gráfico Plotly con atributos por lote. |

Las rutas de exportación no apuntan automáticamente a esta carpeta: algunas son relativas al directorio de ejecución y otras son absolutas de Google Drive. No ejecute sobre los originales ni sobrescriba resultados de referencia. Los mapas interactivos pueden contener identificadores y coordenadas aunque su vista inicial parezca solo una imagen.

## Interpretación del JPG

La imagen representa coeficientes locales, no avalúos ni cambios porcentuales causales. En su escala visible, rojo corresponde a coeficientes negativos y verde a positivos. Para una variable de distancia, un coeficiente negativo indica asociación entre mayor distancia y menor valor, condicionada a la especificación; no equivale a una prueba de valorización causada por el Metro. No debe trasladarse a este JPG la leyenda inversa de otras figuras del notebook.

No se observaron nombres de personas, direcciones, CHIP, códigos de lote ni avalúos individuales visibles; tampoco se detectaron marcadores EXIF o XMP. Su publicación como ilustración técnica resulta razonable bajo la revisión institucional del detalle espacial derivado. No constituye una certificación de anonimización ni de procedencia de la estimación. Se conserva sin cambios y no se ignora automáticamente. Puede incorporarse visualmente al README una vez resueltas las discrepancias de versión, con esta explicación de su escala.

Consulte las [observaciones de reproducibilidad](../README.md#observaciones-para-mejorar-la-reproducibilidad), especialmente las bandas de isócrona, la parametrización GWR y las diferencias entre métricas guardadas y memoria técnica.

## Tama?o y publicaci?n

`dataset_final_predios_completo.csv` mide 136,50 MB y supera 100 MB; `dataset_modelo_lote_umbral100.csv` mide 6,98 MB. Ambos permanecen locales, ignorados y sin rastrear, sin Git LFS, recompresi?n, divisi?n, movimiento ni eliminaci?n. Las salidas tabulares CSV/XLSX de gran tama?o se generan localmente durante la ejecuci?n autorizada del proyecto y no se distribuyen por GitHub. Los HTML tambi?n se excluyen porque pueden incorporar datos por lote.

El JPG mide 0,13 MB y es candidato a documentaci?n p?blica seg?n la revisi?n descrita arriba. Los notebooks tambi?n almacenan resultados fuera de esta carpeta: el de modelos mide 12,95 MB, con aproximadamente 12,78 MB de salidas serializadas. Los tres notebooks conservan outputs, incluidos identificadores prediales.

**Recomendaci?n antes de publicaci?n: limpiar outputs del notebook.** No se han modificado autom?ticamente. La documentaci?n y el c?digo permiten entender el proyecto sin publicar las tablas pesadas; la reproducci?n requiere obtener los insumos institucionales correspondientes.
