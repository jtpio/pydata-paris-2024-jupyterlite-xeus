---
marp: true
paginate: true
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem;
  }
  .center {
    text-align: center;
  }
---

<style>
section::after {
  content: attr(data-marpit-pagination) '/' attr(data-marpit-pagination-total);
}
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
iframe {
  border: none;
}
</style>

![bg fit right:33%](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/icon.svg)

# :bulb: JupyterLite, Emscripten-forge, Xeus, and Mamba

## The computational quartet for in browser interactive computing

### 🗼 PyData Paris 2024

#### :date: 2024-09-25

- :bust_in_silhouette: Jeremy Tuloup
- :bust_in_silhouette: Ian Thomas
- :bust_in_silhouette: Thorsten Beier

---

# About

TODO

---

# What is JupyterLite?

![bg fit right:33%](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/icon.svg)

> JupyterLite is a JupyterLab distribution that runs entirely in the web browser, backed by in-browser language kernels.

---

# "Normal Jupyter"

![center](https://user-images.githubusercontent.com/591645/228267004-e4e2e54f-1d5f-45b7-bacb-6c3a1844c479.png)

---

# JupyterLite

![center](https://user-images.githubusercontent.com/591645/237059523-d29b94e6-7287-4608-b617-b0fe2a74877a.png)

---


# Lightweight Jupyter Frontend running in the browser

![center w:512](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/badge-launch.svg)

- ✅ no Python server
- ✅ no command line
- ✅ no need to install Python and other packages on the user machine
- ✅ can be hosted as a static website

---

# Boots in seconds

![center h:600px](https://user-images.githubusercontent.com/591645/120649478-18258400-c47d-11eb-80e5-185e52ff2702.gif)

---

# The `jupyter-lite` CLI is a **Static Site Generator** (SSG)

```shell
# install the CLI
pip install jupyterlite-core

# build the website
jupyter lite build
```

---

# It generates static assets that can be served easily

<div class="columns">
<div>


```
├── api
│   └── translations
│       ├── all.json
│       └── en.json
├── bootstrap.js
├── build
│   ├── 9507.1e6cc5d.js
│   ├── 9602.62bf0f1.js
│   ├── 9621.e2e8b5d.js
│   ├── ...
│   ├── repl
│   │   ├── bundle.js
│   ├── retro
│   │   ├── bundle.js
│   ├── schemas
│   │   ├── all.json
│   │   ├── @jupyterlab
│   │   │   ├── application-extension
│   │   │   │   ├── commands.json
│   │   │   │   ├── context-menu.json
│   │   │   │   ├── shell.json
│   │   │   │   └── sidebar.json
│   ├── themes
│   │   └── @jupyterlab
│   │       ├── theme-dark-extension
│   │       │   ├── index.css
│   │       │   └── index.js
...
```
</div>
<div>

```
...
│   │       └── theme-light-extension
│   │           ├── index.css
│   │           └── index.js
├── config-utils.js
├── extensions
│       └── xeus-python-kernel
│           └── static
│               ├── numpy-1.24.2-py310h6d2fff6_0.0.data
│               ├── numpy-1.24.2-py310h6d2fff6_0.0.js
│               ├── python-3.10.2-h_hash_26_cpython.0.data
│               ├── python-3.10.2-h_hash_26_cpython.0.js
│               ├── python_data.js
│               ├── remoteEntry.35b4eac217ec6bf078a4.js
├── lab
│   ├── favicon.ico
│   ├── index.html
│   ├── jupyter-lite.ipynb
│   ├── jupyter-lite.json
│   ├── package.json
│   ├── tree
│   │   └── index.html
│   └── workspaces
│       └── index.html
...
```

</div>
</div>

---

# Easy to deploy

Served via well-cacheable, static HTTP(S) on most static web hosts

<div class="columns">
<div>

![center width:256](https://user-images.githubusercontent.com/591645/120675034-00f29080-c495-11eb-928c-26bb94e8eb68.png)
![center width:256](https://user-images.githubusercontent.com/591645/120676545-6dba5a80-c496-11eb-9b2b-604e92c3429b.png)
![center width:256](https://user-images.githubusercontent.com/591645/120675516-6f375300-c495-11eb-819c-d6f1fb3cb0f1.png)

</div>
<div>

![center width:256](https://user-images.githubusercontent.com/591645/120676313-2df37300-c496-11eb-8639-25e2fc606850.png)
![center width:256](https://user-images.githubusercontent.com/591645/236239105-d00f05df-ee79-4062-a0a8-f0f0118bbe1d.png)
![center h:128](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Amazon-S3-Logo.svg/428px-Amazon-S3-Logo.svg.png)

</div>
</div>

---

![bg fit right height:400px](https://user-images.githubusercontent.com/591645/162748538-e44fea00-f727-4055-b795-8f5fc5c6b133.png)

# Standing on the shoulders of giants

-  Built from the ground-up using JupyterLab components and extensions
- The frontend communicates to the in-browser kernels via the Jupyter Protocol

---

# Wasm powered Jupyter running in the browser

- https://developer.mozilla.org/en-US/docs/WebAssembly

![center h:400px](https://user-images.githubusercontent.com/591645/162831191-16956085-783a-435e-b810-0d25da1379b3.png)

---

# :bulb: Interactive Computing in the browser

- Python kernels:
  - Pyodide
  - Xeus Python
- Visualizations:
   - matplotlib
   - ipywidgets
   - plotly
   - and more...

---

# :rocket: Embed a live Python console on your website

![center h:300px](https://user-images.githubusercontent.com/591645/162619390-ecab994a-3f39-4e26-af78-ca2569aee9b2.png)

Embed with:

```html
<iframe
  src="https://jupyterlite.github.io/demo/repl/index.html?kernel=python&toolbar=1"
  width="100%"
  height="500px"
>
</iframe>
```

---

# Or even the full JupyterLab UI

<iframe
  src="https://jtpio.github.io/jupytercon-2023-jupyterlite/lab/index.html?path=demo.ipynb"
  width="100%"
  height="100%"
>
</iframe>

---

# numpy.org

![center](https://user-images.githubusercontent.com/591645/162569443-40e841ad-f42d-44eb-966f-c1c810c1ab10.png)

---

# sympy.org

![center h:500px](https://user-images.githubusercontent.com/591645/167361691-da1252e7-17f4-4bbf-8eee-ba3bfaff8c2e.png)

---

# jupyterlite-sphinx

![center h:500px](https://user-images.githubusercontent.com/591645/162838828-d6407725-15d9-4640-8aa6-c8c8979a9a3f.png)

---

# :rocket: Deploy your own on GitHub Pages

Quickstart: https://github.com/jupyterlite/xeus-python-demo

![center height:400px](https://raw.githubusercontent.com/jupyterlite/xeus-python-demo/main/deploy.gif)

---

# :notebook: Adding notebooks, files and static assets

Create a `notebooks` folder and add a notebook and a CSV file:

```bash
ls notebooks

demo.ipynb iris.csv
```

Build with the `--contents` flag:

```bash
jupyter lite build --contents notebooks
```

---

<video
  controls
  width="100%"
  height="600px"
  src="https://user-images.githubusercontent.com/591645/236281330-8c1c21a3-aec2-4af4-9280-fa65fc330f24.mp4" >
</video>

---

# Deploy static web applications with Voici

![center](https://raw.githubusercontent.com/voila-dashboards/voici/main/docs/voici-logo.svg)

---


# Before

```shell
jupyter lite build --contents notebooks
```

# After

```bash
# build with the Voici CLI
voici build --contents notebooks

# to keep the JupyterLab and Notebook interfaces available
voici build --contents notebooks --apps lab --app retro
```

---

<video
  controls
  width="100%"
  height="600px"
  src="https://user-images.githubusercontent.com/591645/236285012-1c9afa23-8da4-45ea-9b0b-10c5cd2087f0.mp4">
</video>

---

# :muscle: Strengths

- Easy to deploy and scale (static files)
- Interactive computing in the browser accessible to more people
- Simpler for users (no need to install Python and other packages locally)
- Educational use cases
- Reproducibility time capsule

---

# Terminal

![bg fit right:40%](https://raw.githubusercontent.com/jupyterlite/terminal/main/screenshot.png)

JupyterLab

- Terminal connects to a real shell running on the server

JupyterLite

- Now has experimental support for a Terminal running in the browser
- Early stage work in progress

---

<video
  controls
  width="100%"
  height="600px"
  src="https://raw.githubusercontent.com/jtpio/pydata-paris-2024-jupyterlite-xeus/main/img/terminal.m4v">
</video>

---

# The quartet of tools

<div class="columns">
<div>

## JupyterLite

- The browser application

## Emscripten-forge

- Recipes
- Building and uploading packages

</div>
<div>

## Xeus

- Programming language kernels

## Mamba

- Package manager
- Resolving and installing packages

</div>
</div>

<div class="center">
<img width="10%" src="https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/icon.svg">
<img width="20%" src="https://raw.githubusercontent.com/jupyter-xeus/xeus/main/docs/source/xeus.svg">
<img width="30%" src="https://raw.githubusercontent.com/mamba-org/mamba/main/docs/assets/mamba_header.png">
</div>

---

# What is a kernel?

![center](https://raw.githubusercontent.com/jtpio/pydata-paris-2024-jupyterlite-xeus/main/img/kernel.svg)

---

# JupyterLite kernels: pyodide and xeus

![center](https://raw.githubusercontent.com/jtpio/pydata-paris-2024-jupyterlite-xeus/main/img/pyodide-xeus.svg)

---

# Python kernel differences

&nbsp; | pyodide | xeus
--- | ---- | ---- |
Build and package system | pip-based | conda-based
Install packages at runtime | ✅ `%pip install ipympl` | ❌
Supports pre-installed packages | ❌ | ✅
Supports `time.sleep` | ❌ | ✅

---

# :hammer: Emscripten-forge and mamba

## Building WebAssembly packages

platform | pip-based toolchain | conda-based toolchain
--- | ---- | ---- |
noarch, linux, macos, windows | PyPI | conda-forge
emscripten-wasm32 | pyodide | emscripten-forge

---

# How do I use package 'x' in JupyterLite?

- Is it a pure Python package?

  - Noarch wheel from `PyPI` for pyodide
  - Noarch package from `conda-forge` for xeus

- Does it need compiling?

  - `Pyodide` recipe at https://github.com/pyodide/pyodide
  - `Emscripten-forge` recipe at https://github.com/emscripten-forge/recipes

---

# Create a JupyterLite deployment

- Demo repos:

  - For pyodide kernel https://github.com/jupyterlite/demo
  - For xeus-python kernel https://github.com/jupyterlite/xeus-python-demo

- Inputs required:

  - What packages to include (`requirements.txt` or `environment.yml`)?
  - What content to include (notebooks, data files, etc)?
  - Build enviromment (`build-environment.yml`) containing `jupyterlite-core`

---

# Local deployment with both python kernels

<div class="columns">
<div>

`build-environment.yml`:
```yml
name: jlite-build
channels:
  - conda-forge
dependencies:
  - python
  - jupyter_server
  - jupyterlite-core
  - jupyterlite-pyodide-kernel
  - jupyterlite-xeus
```

</div>
<div>

`environment.yml`:
```yml
name: jlite-demo
channels:
  - https://repo.mamba.pm/emscripten-forge
  - conda-forge
dependencies:
  - xeus-python
  - ipympl
  - matplotlib
```

</div>
</div>

Sequence of commands:

```bash
micromamba create -f build-environment.yml
micromamba activate jlite-build
jupyter lite build --contents contents
jupyter lite serve
```

---

# Summary of improvements in the last year

- More stable and easy-to-use build system in Emscripten-forge `rattler-build`
- Experimental Terminal in JupyterLite

# Roadmap

- R kernel
- Proposal to move emscripten-forge to conda-forge

---

# :pray: Thanks!

![bg fit right:33%](https://raw.githubusercontent.com/jupyterlite/jupyterlite/main/docs/_static/icon.svg)

Thanks to all the contributors of JupyterLite, Pyodide, Emscripten Forge, and the Jupyter Community!

- Presentation: https://github.com/jtpio/pydata-paris-2024-jupyterlite-xeus
- Live version: https://jtpio.github.io/pydata-paris-2024-jupyterlite-xeus/files/index.html
