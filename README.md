# Version Bridge for Revit

**Save Revit files to earlier versions, and open files from newer versions, from Revit's own Open and Save As.**

> **Pre-release:** Version Bridge is being tested and the installer has not been published yet. This repository
> holds the documentation and the issue tracker. Watch it to be notified of the first release.

Version Bridge is a free add-in for Autodesk Revit on Windows. It adds earlier versions to Revit's **Save As** dialog
and, when you open a file saved by a newer Revit, offers to convert a copy to your version. Elements stay native and
editable: walls stay walls, families stay families. Nothing is turned into imported geometry.

**Español:** [README.es.md](README.es.md)

## What it does

- **Save As an earlier version.** In Save As, the **Files of type** list shows one entry per earlier version, for
  example *Project Files - Revit 2023 (\*.rvt)*. Choose one, and Version Bridge writes a copy in that version.
- **Open files from newer versions.** When Revit refuses a file saved by a later version, Version Bridge offers to
  convert a copy to your version and open it. By default the copy is saved next to the original as
  `<name>_rvt<year>.rvt`, or you can choose where to save it.
- **The original never changes.** Both features write a separate copy. The copy cannot replace the original file.
- **Projects, families and templates:** `.rvt`, `.rfa`, `.rte` and `.rft`. Family templates (`.rft`) are offered
  next to `.rfa` in Save As > Family.
- **No silent losses.** Each conversion is checked before anything is written. If the file contains data that would
  be dropped and has not been validated as safe to drop, the copy **is not saved**, and Version Bridge tells you why.
- **Local.** Files are converted on your computer. Nothing is uploaded.

## Supported versions

Version Bridge runs in **Revit 2023, 2024, 2025, 2026 and 2027** on 64-bit Windows.

| File saved in | Can be converted to |
| --- | --- |
| Revit 2027 | 2026, 2025, 2024, 2023 |
| Revit 2026 | 2025, 2024, 2023 |
| Revit 2025 | 2024, 2023 |
| Revit 2024 | 2023 |

Revit 2023 is the earliest target, so in Revit 2023 Version Bridge only opens newer files.

## Not supported

- **Workshared models** (central and local files) and **cloud models**: Save As stays Revit's own.
- **Versions earlier than Revit 2023.**
- **Unsaved changes:** the copy is made from the file on disk. If the model has unsaved changes, Version Bridge offers
  to save it first.

## Limitations

Each Revit release adds features that earlier releases do not have. When converting to an earlier version:

- Data that the target version cannot hold is removed. The removals are reported after each conversion.
- Some features cannot be converted at all, for example toposolids when saving to Revit 2023. In that case the
  copy is not saved.

**Keep the original file** and check the converted copy before using it in production: geometry, hosted elements,
families, parameters, schedules, annotations and sheets.

## Download and installation

**Not available yet.** The installer will be published on
[GitHub Releases](https://github.com/SpeedCAD/Version_Bridge_for_Revit/releases), with installation steps. Do not
download installers that claim to be official from any other source.

## Reporting a problem

Open an [issue](https://github.com/SpeedCAD/Version_Bridge_for_Revit/issues/new/choose) with the **Conversion
problem** template. It asks for:

- the Revit version you used, the version of the file and the target version;
- the file type (`.rvt`, `.rfa`, `.rte` or `.rft`);
- what you expected and what happened.

When a conversion fails, Version Bridge writes two logs. Please attach them:

- `%LOCALAPPDATA%\SCADtools\Version Bridge\versionbridge.log`
- `<name>.log.txt`, next to the copy that was not saved: the full conversion report.

The logs contain file paths and element names. Review them before attaching them to a public issue.

**Do not upload confidential models, drawings or client data to public issues.** If the problem only happens with a
model you cannot share publicly, you may send it to **scadtools.software@gmail.com** as a download link (OneDrive,
Google Drive, WeTransfer), mentioning the issue number. Sending it is optional. The model is used only to reproduce
the problem, is not shared with anyone, and is deleted once the issue is closed.

## License

Version Bridge is **free to use** but **not open source**. The add-in and its conversion engine, SCADtools.Bim, are
proprietary. See [LICENSE](LICENSE) for the terms of use and distribution.

For licensing the conversion technology or integrating it in other products, contact SCADtools at
**scadtools.software@gmail.com**.

## Disclaimer

Version Bridge is an independent project. It is not affiliated with, endorsed by or sponsored by Autodesk, Inc.
Autodesk and Revit are registered trademarks of Autodesk, Inc.
