# Kicad pipeline assets
kicad-pipeline-assets provides a reusable toolkit for building consistent, automated KiCad PCB outputs using KiBot and GitHub Actions. It is designed to be consumed as a Git submodule or dependency by hardware projects that require reproducible fabrication, assembly, and documentation pipelines.

### Features
* Modular KiBot YAML library for fabrication, assembly, and documentation workflows
* Reusable GitHub Action for standardized CI-based PCB generation
* Version-controlled KiCad worksheet templates (A3, A4, A5) with Git-aware title blocks
* Shared assets including fonts, color themes, and documentation templates
* Preflight and validation steps (DRC, ERC, stackup checks)
* Example configurations for quick integration

### Repository Structure
* `.github/workflows/` — reusable GitHub Actions workflows
* `.github/actions/` — composite actions for invoking KiBot pipelines
* `kibot/pipelines/` — high-level output pipelines (fabrication, assembly, docs)
* `kibot/filters/` — reusable filters (e.g. manufacturer-specific rules)
* `kibot/preflight/` — validation steps such as ERC/DRC
* `templates/worksheets/` — KiCad drawing templates (.kicad_wks)
* `templates/title_blocks/` — reusable title block components
* `assets/` — fonts, color themes, and documentation templates
* `scripts/` — helper utilities for metadata and BOM processing
* `examples/` — minimal reference project using this repo
* `docs/` — usage and integration documentation

### Usage
As a Git submodule
Add this repository to your project:
```bash
git submodule add https://github.com/alextrical/kicad-pipeline-assets.git tools/kicad-pipeline-assets
git submodule update --init --recursive
```
Reference the provided KiBot pipelines from your project’s configuration:
```text
import:
  - tools/kicad-pipeline-assets/kibot/pipelines/fabrication.yml
```
### With GitHub Actions
Use the reusable workflow:
```text
jobs:
  pcb:
    uses: alextrical/kicad-pipeline-assets/.github/workflows/reusable-kibot.yml@main
    with:
      pipeline: fabrication
```
### Design Goals
* Reproducible outputs across projects and teams
* Minimal per-project configuration
* Composable and modular pipeline definitions
* Clean separation between project design and build infrastructure
* Compatibility with Git submodule-based workflows

### Requirements
* KiCad (version aligned with your pipelines)
* KiBot
* GitHub Actions (for CI usage)

### Contributing
Contributions are welcome, particularly:
* New pipeline modules
* Manufacturer-specific filters
* Improved documentation templates
* Additional worksheet formats

License
See LICENSE file for details.