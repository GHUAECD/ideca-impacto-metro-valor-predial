# Fuentes de información

Los archivos de datos se mantienen localmente y no se distribuyen automáticamente con el repositorio público. La memoria técnica atribuye varias capas a datos abiertos Bogotá y otras al proyecto; esa descripción no constituye una autorización general para redistribuir todos los archivos. No se incluyen registros individuales ni rutas institucionales en esta guía.

## Inventario inspeccionado

| Archivo local | Contenido confirmado y finalidad |
| --- | --- |
| `BaseDatosGD.gdb-20260810T154550Z-1-001.zip` | Contiene `BaseDatosGD.gdb`. Su catálogo interno identifica `Predios_GD`, `Lote`, `LoteData`, `EstacionesLinea1` y `TrazadoLinea1`, utilizados por el código para delimitar lotes, incorporar geometría, áreas y avalúo 2026, y calcular proximidad al Metro. También figuran otras capas, como `SueloProtegido` y capas de Línea 2, que no forman parte de la especificación principal. |
| `bd_uaecd_2026.gdb-20260810T154558Z-1-001.zip` | Contiene `bd_uaecd_2026.gdb`. El catálogo confirma `Predio` y `Calificacion`; el código obtiene atributos catastrales, uso, PH, estrato, destino, sector y dirección. También contiene otras tablas no utilizadas en el flujo principal. |
| `Predio-20260810T154644Z-1-001.zip` | Contiene la carpeta `Predio/`, con conjuntos shapefile `LOTE`, `ZonaPiloto15Min` y `Estación_troncal`, y una tabla `PREDIO.dbf`. No aparece `PREDIO.shp`: no debe describirse como un shapefile de predios completo. `Estación_troncal` corresponde al insumo de TransMilenio; el código no lee este ZIP directamente. |
| `Zona_piloto_GD.gpkg` | El catálogo confirma `Colegios122025`, `IES`, `ips`, `parques`, `Estación_troncal`, capas con prefijo `BaseDatosGD —` y `layer_styles`. El flujo usa parques, colegios e IES; no utiliza la capa `ips` como sustituto del shapefile de salud corregido. |

La inspección consultó los listados ZIP y los nombres del catálogo de las GDB en memoria, y los metadatos SQLite del GeoPackage en modo de solo lectura. No se extrajeron permanentemente los ZIP ni se validaron todos los registros de sus capas.

## Insumos adicionales requeridos

| Insumo referenciado | Uso y disponibilidad |
| --- | --- |
| `Estación_troncal.shp` y archivos acompañantes | Distancias a estaciones de TransMilenio. Está dentro del ZIP `Predio`; debe habilitarse en una copia de trabajo autorizada. |
| `Isócronas.shp` y archivos acompañantes | Clasificación por `FacilityID`, `FromBreak` y `ToBreak`. No se encontró ese shapefile en el inventario ni en los listados ZIP. `ZonaPiloto15Min` no puede asumirse equivalente. |
| `salida.shp` y archivos acompañantes | IPS corregidas, con campo `lotcodigo`, para distancia a salud y correspondencia con lotes. No se encontró. La capa `ips` del GeoPackage no tiene equivalencia demostrada con este insumo. |
| `SECTOR.shp` y archivos acompañantes | Análisis territorial del notebook de modelos mediante `SCACODIGO` y, cuando existe, `SCANOMBRE`. No se encontró ese shapefile. La tabla `SCat` en la GDB no reemplaza automáticamente la lectura implementada. |
| Fuentes de ofertas de venta/arriendo | La memoria describe un contraste independiente. No se identificó una base inequívoca de ofertas ni se entregó su notebook. Los tres notebooks disponibles no ajustan modelos de ofertas. |

El nombre usado por el código para colegios es `colegios122025`, mientras el catálogo contiene `Colegios122025`: debe verificarse la resolución del nombre por el controlador, sin presuponer que todos los entornos ignoran mayúsculas.

## Organización para reproducir

Conserve los cuatro archivos originales en esta carpeta. En una ubicación de trabajo separada, habilite las GDB con sus nombres originales, el GeoPackage y los conjuntos shapefile completos; no basta con un `.shp` sin su tabla, índice y referencia espacial. Obtenga los insumos faltantes mediante los canales autorizados de la entidad.

Los notebooks esperan rutas absolutas de Google Drive y no buscan automáticamente los archivos en `2 - Fuentes/`. Su ejecución requiere preparar esas ubicaciones en un entorno autorizado o adaptar rutas en copias independientes. No se han cambiado las rutas originales. `Consignacion_base_de_datos.ipynb` utiliza `EPSG:6247` como CRS de trabajo y produce el CSV que consume la preparación; consulte el [flujo completo](../README.md#flujo-de-ejecución).

Las versiones de Python, bibliotecas y fuentes deben registrarse al preparar una reproducción. La entrega actual no incluye un entorno bloqueado ni todos los insumos auxiliares necesarios.

## Archivos pesados y distribuci?n local

Las fuentes no se distribuyen por GitHub ni por Git LFS. El ZIP institucional UAECD mide 983,19 MB, el ZIP `Predio` 392,39 MB y el GeoPackage 220,77 MB; los tres superan 100 MB y permanecen ignorados y sin rastrear. El ZIP `BaseDatosGD`, de 34,79 MB, tambi?n est? excluido.

El usuario debe proveer u obtener los insumos de las fuentes institucionales correspondientes, con las autorizaciones aplicables. No se ofrecen enlaces de descarga no confirmados. Los archivos originales permanecen locales, sin nueva compresi?n, divisi?n, movimiento ni eliminaci?n. El repositorio documenta su funci?n y requisitos para que el proyecto pueda entenderse sin distribuirlos.
