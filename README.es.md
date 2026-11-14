# Version Bridge for Revit

**Guarde archivos de Revit en versiones anteriores y abra archivos de versiones posteriores, desde Abrir y Guardar
como de Revit.**

> **Versión preliminar:** Version Bridge está en pruebas y el instalador aún no se publica. Este repositorio contiene
> la documentación y el registro de issues. Sígalo para enterarse de la primera versión.

Version Bridge es un complemento gratuito para Autodesk Revit en Windows. Agrega las versiones anteriores al cuadro
**Guardar como** y, cuando abre un archivo guardado por un Revit más nuevo, ofrece convertir una copia a su versión.
Los elementos siguen siendo nativos y editables: los muros siguen siendo muros y las familias, familias. Nada se
convierte en geometría importada.

**English:** [README.md](README.md)

## Qué hace

- **Guardar como en una versión anterior.** En Guardar como, la lista **Tipo de archivo** muestra una entrada por
  cada versión anterior, por ejemplo *Archivos de proyecto - Revit 2023 (\*.rvt)*. Elija una y Version Bridge
  escribe una copia en esa versión.
- **Abrir archivos de versiones posteriores.** Cuando Revit rechaza un archivo guardado por una versión posterior,
  Version Bridge ofrece convertir una copia a su versión y abrirla. Por omisión, la copia se guarda junto al original
  como `<nombre>_rvt<año>.rvt`; también puede elegir dónde guardarla.
- **El original nunca cambia.** Las dos funciones escriben una copia aparte, que no puede reemplazar al archivo
  original.
- **Proyectos, familias y plantillas:** `.rvt`, `.rfa`, `.rte` y `.rft`. Las plantillas de familia (`.rft`) se ofrecen
  junto a `.rfa` en Guardar como > Familia.
- **Sin pérdidas silenciosas.** Cada conversión se comprueba antes de escribir nada. Si el archivo tiene datos que se
  perderían y cuya eliminación no se ha validado, la copia **no se guarda** y Version Bridge explica el motivo.
- **Local.** Los archivos se convierten en su computador. No se sube nada.

## Versiones compatibles

Version Bridge funciona en **Revit 2023, 2024, 2025, 2026 y 2027** sobre Windows de 64 bits.

| Archivo guardado en | Se puede convertir a |
| --- | --- |
| Revit 2027 | 2026, 2025, 2024, 2023 |
| Revit 2026 | 2025, 2024, 2023 |
| Revit 2025 | 2024, 2023 |
| Revit 2024 | 2023 |

Revit 2023 es la versión de destino más antigua: en Revit 2023, Version Bridge solo abre archivos más nuevos.

## No compatible

- **Modelos con worksharing** (archivos centrales y locales) y **modelos en la nube**: Guardar como sigue siendo el
  de Revit.
- **Versiones anteriores a Revit 2023.**
- **Cambios sin guardar:** la copia se hace desde el archivo en disco. Si el modelo tiene cambios sin guardar,
  Version Bridge ofrece guardarlo primero.

## Limitaciones

Cada versión de Revit agrega funciones que las anteriores no tienen. Al convertir a una versión anterior:

- Se eliminan los datos que la versión de destino no puede contener. Cuando la copia se guarda, Version Bridge
  muestra solo dónde quedó. Lo eliminado se informa solo cuando la copia no se guarda, en su registro (vea
  [Informar un problema](#informar-un-problema)).
- Algunas funciones no se pueden convertir, por ejemplo los toposólidos al guardar en Revit 2023. En ese caso la copia
  no se guarda.

**Conserve el archivo original** y revise la copia convertida antes de usarla en producción: geometría, elementos
alojados, familias, parámetros, tablas, anotaciones y planos.

## Descarga e instalación

**Aún no está disponible.** El instalador se publicará en
[GitHub Releases](https://github.com/SpeedCAD/Version_Bridge_for_Revit/releases), con los pasos de instalación. No
descargue instaladores que digan ser oficiales desde otros sitios.

## Informar un problema

Abra un [issue](https://github.com/SpeedCAD/Version_Bridge_for_Revit/issues/new/choose) con la plantilla
**Conversion problem**, que pide:

- la versión de Revit que usó, la versión del archivo y la versión de destino;
- el tipo de archivo (`.rvt`, `.rfa`, `.rte` o `.rft`);
- qué esperaba y qué ocurrió.

Cuando una conversión falla, Version Bridge escribe dos registros. Adjúntelos, por favor:

- `%LOCALAPPDATA%\SCADtools\Version Bridge\versionbridge.log`
- `<nombre>.log.txt`, junto a la copia que no se guardó: el informe completo de la conversión.

Los registros contienen rutas de archivos y nombres de elementos. Revíselos antes de adjuntarlos a un issue público.

**No suba modelos, planos ni datos de clientes confidenciales a issues públicos.** Si el problema solo ocurre con un
modelo que no puede compartir públicamente, puede enviarlo a **scadtools.software@gmail.com** como enlace de descarga
(OneDrive, Google Drive, WeTransfer), con el número del issue. Enviarlo es opcional. El modelo se usa solo para
reproducir el problema, no se comparte con nadie y se elimina cuando el issue se cierra.

## Licencia

Version Bridge es **de uso gratuito**, pero **no es de código abierto**. El complemento y su motor de conversión,
SCADtools.Bim, son propietarios. Los términos de uso y distribución están en [LICENSE](LICENSE) (inglés, la versión que prevalece) y en
[LICENSE.es.txt](LICENSE.es.txt) (traducción).

Para licenciar la tecnología de conversión o integrarla en otros productos, escriba a SCADtools a
**scadtools.software@gmail.com**.

## Aviso

Version Bridge es un proyecto independiente. No está afiliado a Autodesk, Inc., ni cuenta con su respaldo o
patrocinio. Autodesk y Revit son marcas registradas de Autodesk, Inc.
