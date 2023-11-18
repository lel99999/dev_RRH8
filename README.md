# dev_RRH8
Workspace and Development for  R on RHEL8

#### Download URLs
- [EPEL 8](https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm) <br/>
- [R_VERSION](https://cdn.rstudio.com/r/centos-8/pkgs/R-${R_VERSION}-1-1.x86_64.rpm) <br/>

#### GDAL 3.0.4 for RHEL 8.x 
- [https://download.osgeo.org/gdal/3.0.4/](https://download.osgeo.org/gdal/3.0.4/) <br/>

- NOTES:  GDAL v3.7.3 on RHEL 8 requires: <br/>
  - cmake <br/>
  - Will get errors GDALAllRegister not found in libgdal <br/>

#### GDAL 3.0.4 Error jpeg2000
```
$sudo make clean
$ ./configure --with-libtiff=internal --with-geotiff=internal --with-jpeg=internal --with-jpeg12
$sudo make install
```

#### Patch / Fixes
- Install python27 for yum
- `$sudo dnf module install python27`
- If rstudio-2023 is required to be installed with rstudio-server-2023
- `$sudo rpm -Uvh https://download1.rstudio.org/electron/rhel8/x86_64/rstudio-2023.06.2-561-x86_64.rpm --force` <br/>

#### Missing RPMs/Libraries
R package xml2: <br/>
- cairo-devel
- libxml2-devel
- harfbuzz-devel
- fribidi-devel

R package RPostgreSQL: <br/>
- freetype-devel
- libpng-devel
- libtiff-devel
- libjpeg-turbo-devel
- libpq-devel
- libpq5-devel
