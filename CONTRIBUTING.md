# Guía de contribución

Las contribuciones deben mantener la trazabilidad entre fuentes, preparación de datos, especificación de modelos y resultados. Preserve los originales entregados; realice las pruebas en copias de trabajo y directorios separados, sin sobrescribir los resultados de referencia.

1. Haga un fork del repositorio.
2. Cree una rama descriptiva, por ejemplo `docs/aclarar-metodologia`.
3. Realice un cambio acotado y explique su propósito. Evite renombrar, mover o reformatear archivos ajenos al cambio.
4. Documente cualquier modificación metodológica: motivo, variables afectadas, metodología, efecto esperado y método de validación. Distinga asociaciones estadísticas de inferencias causales.
5. Valide los notebooks: compruebe su estructura, imports, rutas, insumos y orden de celdas. Cuando el cambio requiera ejecución, utilice un entorno aislado y datos autorizados, conserve los originales y registre versiones, parámetros, semillas y métricas. Si faltan fuentes, informe qué no pudo validar; no declare una ejecución completa.
6. Abra un Pull Request con el problema, los cambios, la evidencia de validación y las limitaciones. Revise el diff completo antes de enviarlo.

No incluya bases institucionales, GeoDatabases, GeoPackages con información no autorizada, CSV de resultados masivos, credenciales, tokens ni información sensible. Esta restricción también aplica a archivos comprimidos, XLSX, imágenes, mapas interactivos, metadatos y salidas incrustadas en notebooks. Los notebooks originales contienen resultados guardados con identificadores prediales: su publicación necesita una revisión específica; `.gitignore` no elimina esos contenidos.

Para cambios de modelos, indique la unidad de análisis, variable objetivo, agregación, exclusiones, matriz de pesos espaciales, parametrización GWR y diseño de validación. Diferencie métricas de entrenamiento, validación cruzada y validación espacial. Informe si los resultados cambian respecto de la memoria técnica.

No suponga que un archivo está protegido solo porque aparece en `.gitignore`: compruebe también si Git ya lo rastrea. No retire archivos del índice ni cambie licencias sin un alcance explícito. Consulte las discrepancias pendientes en [README.md](README.md#observaciones-para-mejorar-la-reproducibilidad).
