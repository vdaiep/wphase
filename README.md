# W phase inversion - Installation instructions
**Z.Duputel, L.Rivera and H.Kanamori**

For a complete documentation, please refer to <http://wphase.unistra.fr/wiki/doku.php/wphase>

## Dependencies

* gcc, gfortran
* rdseed 
* python 
* for MacOS users, it is necessary to install Coreutils which provide GNU Core Utilities. This can be done using fink,macports or homebrew 
* (*optional; for graphical output*) python modules: Numpy, Matplotlib, Basemap and netCDF4.
* (*optional; for graphical output*) GMT4


## Building/Installing 

Add the following environnement variables to the '.tcshrc' file in your home directory (or alternativelly '.cshrc'/'.bashrc' depending on the shell you are using):

```
setenv WPHASE_HOME 'path to W-phase inversion directory' 
setenv GF_PATH     'path to Green's Functions data base' 
setenv RDSEED      'path to the rdseed executable'
```

(*optional, see bellow*) 
```
setenv ETOPOFILE 'path to ETOPO netCDF file'
```

We strongly advise to separate the ${WPHASE_HOME} directory
(i.e. the directory containing "bin" and "src") from the run
directories (i.e. containing data, and output files). This is
to make easier further updates. A good idea could be also to 
add ${WPHASE_HOME}/bin path to the $PATH of your shell.

Before compiling, 

* If you are using 32 bits libraries on a 64 architecture, please add the flag '-m32' to OPTFLAG. 
* Be sure the environment variables described above are assigned.

Once all is ready, a simple 'make' or 'make -B' in $WPHASE_HOME/src/ 
should then build the whole package.

*OPTIONAL; to include the topography/bathymetry in the grid-search graphical output.*


## Using ETOPO01 Global Relief Model

ETOPO01 is a 1 arc-minute global relief model of the Earth's surface
provided by Amante et al. (2009):  
<http://www.ngdc.noaa.gov/mgg/global/global.html>

If Basemap is installed, you can optionally draw ETOPO01 topography and
bathymetry. To do so, the path to the ETOPO01 netCDF file must be
assigned to the environment variable $ETOPOFILE which can be
done in your .tcshrc fil (or .bachrc, .cshrc, etc.). The make_grids.py
script have been fully tested for grid-registered netCDF file of the
ETOPO1 bedrock file available at:  
<http://www.ngdc.noaa.gov/mgg/global/relief/ETOPO1/data/bedrock/grid_registered/netcdf/ETOPO1_Bed_g_gmt4.grd.gz>


## References
Amante, C. and B. W. Eakins, ETOPO1 1 Arc-Minute Global Relief Model:
Procedures, Data Sources and Analysis. NOAA Technical Memorandum
NESDIS NGDC-24, 19 pp, March 2009.


**Report bugs to: <zacharie.duputel@unistra.fr>**