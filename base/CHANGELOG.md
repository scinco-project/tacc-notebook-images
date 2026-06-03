# Change Log
All notable changes to this project will be documented in this file.

## 2.0.0 - 2026-06-03

### Breaking Changes:
- Base image switched from `taccsciapps/jupyteruser-base` to `jupyter/minimal-notebook:latest`.
- All package versions updated to current releases.
- `dash-core-components`, `dash-html-components`, `dash-renderer`, and `dash-table` removed as standalone packages — bundled into `dash` 2.0+.

### New features:
- Defaults to Jupyter Lab instead of older UI

### Removed:
- Dropped abandoned/defunct packages: `algorithmia`, `algorithmia-api-client`, `dashserve`, `dash-table-experiments`, `jupyter-plotly-dash`, `jupyterlab-dash`, `nbserverproxy`, `mydcc`, `dpd-components`, `import-ipynb`.
- Dropped `appnope`, `enum34`, `keras` (included with `tensorflow` as `tf.keras`).
- Dropped `Django`, `django-plotly-dash`, `sqlparse`, `zope.interface`.
- Dropped ~65 packages redundant with `jupyter/minimal-notebook` base image.

### Bug fixes:
- Warning that Jupyter Lab needs to be built.


## 1.0.0 - 2021-10-28
Initial commit of the repo files. 

### Breaking Changes:
- Initial release.

### New features:
 - Initial release.

### Bug fixes:
- None.
