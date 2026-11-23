# ECO_RET

### Ecological Retrofitting of Existing Suburbs

**ECO_RET** is a GIS-based spatial decision-support tool for diagnosing existing suburban areas, evaluating their ecological urbanisation potential, and identifying plots suitable for sustainable spatial interventions. It supports the transition from monofunctional suburbs towards more accessible, self-sufficient and environmentally responsible neighbourhoods, consistent with the **15-minute city** concept.

ECO_RET was developed at **Gdansk University of Technology** as part of research supported by **IDUB ARGENTUM**.

## What is ECO_RET?

ECO_RET is an automated analytical workflow created in the **QGIS Graphical Modeler**. It integrates land use, transport, public services, green infrastructure, planning regulations and cadastral plots to support transparent, repeatable spatial assessments. It is a QGIS processing model (`.model3`), **not** a conventional Python plugin.

## Analytical framework

The workflow consists of five complementary components:

| Component | Scope |
| --- | --- |
| **01. Conditions of the analysed suburbs** | Study-area boundaries, terrain, protected areas and hazards, demographics, property prices, and space syntax |
| **02. Analysis of suburban development** | Land use, transport, local spatial development plans (MPZP), services, and plots for development |
| **03. Access to urban infrastructure** | Accessibility to managed green spaces, primary schools, kindergartens, public-transport stops, public spaces, public services and third places |
| **04. Analysis of ecological urbanisation potential** | Multi-criteria assessment and selection of plots with transformation potential |
| **05. Development vision generator** | Rule-based assignment of potential ecological interventions to selected plots |

Some analyses in Component 01 are conducted separately from the main model, as described in the user manual.

## Getting started

1. Install **QGIS** with its Processing framework enabled.
2. Download the `.model3` file from this repository.
3. In QGIS, open the **Processing Model Designer** and load the downloaded model (or add it to your local Processing models directory).
4. Prepare the required input spatial datasets and styles, following the *ECO_RET User Manual*.
5. Check the model parameters and update any paths referring to the original research environment, including input/output GeoPackages and QGIS layer-style (`.qml`) files.
6. Ensure that any third-party algorithms used by the model are installed and configured before running it. Check the Processing toolbox for missing providers.
7. Run the model and inspect the resulting spatial layers.

**Important:** This repository's `.model3` file alone is not a complete ready-to-run dataset. Running the workflow requires suitable, correctly structured input data. The exact QGIS version and third-party dependency compatibility should be verified before a reproducible release is declared.

## Input data

The workflow uses spatial datasets prepared and standardised for each component, primarily as **GeoPackage (`.gpkg`)** files. Depending on the analysis, inputs include:

- Boundaries of the study area and administrative units
- Digital terrain model and environmental constraints
- Population and property-price information
- Land use, buildings, road and public-transport networks
- Local spatial development plans (MPZP)
- Schools, kindergartens, public services, public spaces and third places
- Cadastral plots and relevant attributes
- QGIS layer styles (`.qml`)

Potential sources described in the manual include public geospatial registers, Statistics Poland (GUS), OpenStreetMap, municipal spatial information systems and original research datasets. Data must be harmonised in coordinate reference system, attribute structure and spatial extent, and checked for topology and duplicates.

Space syntax analysis is described as an external step using **DepthmapX**. Some model operations may require additional QGIS Processing providers; verify their availability in your installation.

## Outputs

ECO_RET produces intermediate analytical layers and a final layer of plots selected for possible intervention. Results are stored in spatial datasets, including GeoPackages.

The final attribute table can contain an **`INTERVENTION`** text field with one or more recommended ecological solutions for each eligible plot. Recommendations may concern:

- Housing and shared-resource solutions
- Walking, cycling and public-transport infrastructure
- Managed green spaces, water retention and rain gardens
- Renewable-energy infrastructure
- Educational, healthcare, social and other local services

The intervention-assignment rules are described in the user manual and use fields including `pole`, `GRUPA_REJE`, `PRZEZNACZE`, `PRZEZNACZE2Legenda`, `Access`, `Access_2`–`Access_7` and `INTERVENTION`. Field names and planning designations must be adapted where local datasets differ. The manual describes using QGIS Field Calculator to apply the full expression; this should not be assumed to run automatically as part of the `.model3` file.

**ECO_RET provides decision-support recommendations, not approved designs or investment permissions.** Local legal, environmental and technical feasibility must be assessed separately.

## Documentation

See the English **ECO_RET User Manual** for the detailed methodological framework, input/output data specifications, individual analyses, intervention rules and examples. Upload the manual to this repository alongside the model, preferably also in PDF format.

## Intended users

- Urban and regional planners
- Local authorities and public-sector analysts
- GIS researchers and spatial-data specialists
- Landscape architects and urban designers
- Teams involved in participatory spatial planning

## Research and acknowledgements

Developed at **Gdansk University of Technology**, with support from the **IDUB ARGENTUM** research programme.

**Authors, institutional rights, funding acknowledgement and preferred citation:** to be confirmed before the first public release.

## License and citation

Before adding a software license, confirm that the rights holders authorise public distribution and the selected license. A `LICENSE` file and `CITATION.cff` should be added once the approved license, author list, release version and citation details are confirmed.

## Project status

**Research model / initial public repository.** The workflow and its external dependencies should be tested on a clean QGIS installation with documented sample input data before describing the project as fully reproducible.
