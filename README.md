# Shipboard ADCP STA processing

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/olakal/sadcp-sta-processing/blob/main/SADCP_STAprocc_colab.ipynb) 

`SADCP_STAprocc_colab.ipynb`

A simple Google Colab workflow for reading, quality controlling, visualizing,
and exporting shipboard ADCP data collected with Teledyne RDI instruments
using VmDas.

The notebook is intended to be easy to use without requiring Python
programming experience.

### Long version

[![Open Long Version in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/olakal/sadcp-sta-processing/blob/main/SADCP_STAprocc_long_colab.ipynb) 

`SADCP_STAprocc_long_colab.ipynb`

Detailed version intended for learning and QC inspection. Shows the
individual QC steps and additional diagnostic plots.

## Supported instruments

The current version supports:

- Teledyne RDI WorkHorse 
- Teledyne RDI Ocean Surveyor 

Input data are VmDas Short Term Average (`.STA`) files. These files contain time-averaged ADCP measurements, including current velocity and direction at multiple depth bins, together with supporting information such as time, position, depth, and instrument data.

## Getting started

No local Python installation is required.

1. Go to https://colab.research.google.com/
2. Select **Upload notebook**.
3. Upload `SADCP_STAprocc_colab.ipynb`.
4. Follow the instructions in the notebook and run the cells from top to bottom.
5. When requested, upload one `.STA` file.
6. Download the processed results at the end of the notebook.

See the PDF instructions in this repository for a more detailed step-by-step guide.

## Quality control

The notebook applies basic automatic quality control based on:

- beam correlation
- error velocity
- percent good
- bottom-track depth
- sidelobe interference near the bottom

Instrument-specific settings are used for the WH600 and OS150.

The automatic QC is intended as a first-level screening. The resulting
figures should always be visually inspected.

## Output

The notebook can produce:

- ship-track map
- current velocity plots
- QC summary
- CSV file with processed current data
- NetCDF file with processed current data and metadata

Rejected velocity measurements are stored as missing values in the NetCDF
output.

## Test data

Two example `.STA` files are included:

- one WH600 example
- one OS150 example

These can be used to test the notebook before processing other data.

## Time and position

The main time coordinate is the ADCP instrument time (UTC).

Navigation information is read from the VmDas navigation data stored in the
STA file. Positions are screened for invalid or physically implausible
navigation values.

## Important

This is a processing and QC tool, not a fully automated final data-quality
assessment. Users should inspect the resulting plots and consider the
measurement conditions before using the processed data for analysis.

## Contact

ola.kalen@smhi.se
Swedish Meteorological and Hydrological Institute (SMHI)  
Swedish National Oceanographic Data Centre (NODC Sweden)
