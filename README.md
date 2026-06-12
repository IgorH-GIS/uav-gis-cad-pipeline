UAV-Derived Infrastructure Mapping & Automated GIS-CAD Pipeline 

Project Overview: This project demonstrates an end-to-end spatial data pipeline, transforming high-resolution UAV (drone) imagery into standardized, engineering-ready CAD deliverables and automated Python-based spatial reports. Based on a residential block in Sunderland, UK, the workflow highlights advanced topological digitization, strict GIS-CAD interoperability, and PyQGIS automation designed for high-volume Data-as-a-Service (DaaS) operations. 

Core Technologies: QGIS, PyQGIS (Python), GeoPackage, LibreCAD, DXF. Coordinate Reference System: EPSG:32630 (WGS 84 / UTM zone 30N). 

Phase 1: Feature Extraction & Topologically Rigorous Digitization 

 

The initial phase focused on extracting actionable vector data from the raw UAV orthophoto. 

Topological Integrity: Digitized building footprints utilizing advanced snapping parameters. This ensured a strictly topologically correct vector layer with zero overlaps or gaps between adjacent terraced structures, critical for accurate downstream area calculations. 

Relational Database Structuring: Centralized ground infrastructure assets (e.g., manholes, lamp posts) within a single .gpkg (GeoPackage) layer. Feature differentiation was managed via strict string attribute fields rather than fragmented geometries, laying the groundwork for programmatic filtering. 

Phase 2: Interoperability & CAD Standardization 

 

Translating spatial data into engineering environments requires strict adherence to industry drafting standards. 

Scale Validation: Verified metric retention during the DXF export, confirming a 1:1 absolute spatial scale (e.g., building facade dimensions exactly matching 9.92m in the CAD environment). 

Data Hygiene & "By Layer" Inheritance: Resolved common GIS-to-CAD translation quirks where features retain hardcoded export colors. Processed the .dxf entities to enforce strict "By Layer" property inheritance, ensuring that architectural outlines and utility nodes automatically respond to the CAD layer manager. This resulted in a clean, standardized, and immediately deployable base map for civil engineers. 

Phase 3: PyQGIS Automation & Conditional Spatial Analysis 

 

To eliminate manual geoprocessing and expedite reporting, a custom Python script was developed using the PyQGIS API to perform simultaneous data extraction and conditional spatial analysis. 

Automated Coordinate Reporting: The script iterates through the infrastructure database, applying logical string filtering to isolate utility nodes (manhole). It dynamically extracts their precise X/Y spatial coordinates (EPSG:32630) and generates an automated console report ready for surveying hardware. 

Selective Buffering via API: The script conditionally identifies structural lighting elements (lamp_post) and parses them into QGIS's native geoprocessing core using the QgsProcessingFeatureSourceDefinition class. 

Spatial Output: Automatically rendered 15-meter illumination buffer zones exclusively around the filtered features as a temporary memory layer, visually validating street-level lighting coverage against the residential boundaries. 

Business Impact: This automated pipeline bridges the gap between raw UAV acquisition and actionable engineering design. By enforcing topological rules, ensuring CAD compatibility, and automating spatial analysis via Python, this workflow drastically reduces manual processing time and delivers scalable, high-quality spatial intelligence suitable for modern GIS and architectural workflows. 
