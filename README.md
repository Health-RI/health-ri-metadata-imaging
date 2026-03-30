# Health-RI Imaging metadata model

> This repository on imaging metadata is work in progress. For the official Health-RI metadata model v2 for
> general health data, see the following GitHub repository: [Health-RI metadata](https://github.com/Health-RI/health-ri-metadata).
 
This metadata model is intended to better describe imaging datasets with the purpose of increasing findability in a catalogue. The metadata will therefore be on an dataset, i.e., aggregated, level. For this initial version, the scope of this model has been limited to radiological imaging data; other imaging disciplines, e.g., pathology and opthamology, and derived data were not included in this version.

This model is designed to be an extension of the Health-RI v2 metadata model, currently the most recent version is [version 2.0.2](https://github.com/Health-RI/health-ri-metadata/tree/v2.0.2).

![](./Imaging%20Metadata%20Model.png)

Newly introduced classes:
- ImagingSessionProtocol
  - An ImagingSessionProtocol describes a protocol used for creating the imaging sessions in this dataset. An imaging session is defined as an event which clinically would result in one report. An imaging session consists of one or more scans. This corresponds to the level of a DICOM Study.
  - Subclass of Procedure (http://semanticscience.org/resource/SIO_000999)
  - For CT, MR and PET scans, ImagingSessionProtocol can be subclassed into CTImagingSessionProtocol, MRImagingSessionProtocol and PETImagingSessionProtocol respectively. For other imaging modalities the generic case can be used.
- ScanProtocol
  - ScanProtocol describes the protocol used for one or multiple acquisitions (slices) using the same parameters on a patient, as part of an imaging session. This corresponds to the level of a DICOM Series.
  - Subclass of Procedure (http://semanticscience.org/resource/SIO_000999)
  - For CT, MR and PET scans, ScanProtocol can be subclassed into CTScanProtocol, MRScanProtocol and PETScanProtocol respectively. For other imaging modalities the generic case can be used.

# Development

Any questions and other issues can be submitted through 'Issues'. If you are inclined to suggest changes yourself,
please check in with the maintainers first through an Issue. All Pull requests are welcome, but there is no guarantee
that your changes will be integrated. 

## Script 'split-csv'
In order to both give uses the accessibility of modifying a single Excel file when developing the model, and 
to give insights in the changes, a script 'split-csv' has been added. 
After committing a change in the Excel file 'Health-RI Imaging Metadata model {version}.xlsx', a Github Actions
workflow will run and split each sheet into a separate CSV file. These files will be added to the folder 'csv' 
and committed. The new commit will be called 'split-csv: {title of original commit}' and can be used to see 
the changes.