---
kind: build_system
name: No Build System — Single-File Static App
category: build_system
scope:
    - '**'
source_files:
    - index.html
---

This repository contains only a single `index.html` file and has no build system, build scripts, CI configuration, containerization files, or dependency manifests. The project is a vanilla single-page Thai-language calorie & macro tracker that runs directly in the browser with no compilation, bundling, or packaging step. There are no Makefiles, Dockerfiles, package.json, webpack/vite/rollup configs, or any other build-related artifacts to analyze.