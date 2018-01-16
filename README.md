# Marine-Charts
Collection of Marine Charts, Maps and Images with projections for underwater vehicle mission planning.

## NOAA, Office of Coast Survey
### Nautical Charts of US Coasts and Great Lakes
<http://www.charts.noaa.gov/InteractiveCatalog/nrnc.shtml>

There are two forms of electronic charts available for download, RNC and ENC, Rastor Navigational Chart and Electronic Navigational Chart respectively. The RNC file will load into QGIS like a normal navigational chart on one layer. This single layer will show depths, shipping lanes, navigational buoys etc. The ENC file will load as multiple vecter layers. Each layer will represent some property as either a polygon, line, or point. The ENC file will have a file extention of ".000" along with some text files. The RNC file will consist of ".KAP" files with ".BSB" files to translate and rotate the image to the correct projection.

For AUV mission planning both filetypes are useful. The RNC files will show working depths and areas to keep out of or away from like high traffic areas and shipwrecks. The ENC files may show what type of bottom is in a certain area, such as coral, sand or alge.

#### Software Compatibility

OceanServer's VectorMap v8.0 mission planning software seems to open either of these filetypes.

QGIS v2.18.14 will open the ENC vector file as a vector layer.

QGIS v2.18.14 cannot correctly open the RNC files. They need to be converted to GeoTIFF first.
To convert from BSB and KAP to GeoTIFF, using the Oahu 19359 RNC chart as an example:

First convert the KAP and BSB file to .tif using gdal_translate: 
    $ gdal_translate -of GTiff 19359_1.KAP 19359_1.tif

Second reproject to WGS84 (geodetic projection) to import in QGIS:
    $ gdalwarp -t_srs EPSG:4326 19359_1.tif 19359_1_wgs.tif

Example code found here:
    gist.github.com/colemanm/4587067

## Hawai'i Mapping Research Group
### Bathymetric and Backscatter of Main Hawaiian Islands
<http://www.soest.hawaii.edu/HMRG/multibeam/index.php>
