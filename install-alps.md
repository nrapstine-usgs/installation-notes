#### Installing ALPS

Login to Yeti

Load appropriate modules:

```bash
cmake/3.10.1 
```

Then make directory or navigate where you want ALPS to be installed.

```bash
mkdir opt
cd opt
mkdir alps
cd alps
git clone https://github.com/dnagle-usgs/lidar-processing.git
mkdir build
```

We need to exclude `gdal` targets from building (they fail to build) and Yeti already has `gdal` installed:

```
cd lidar-processing/install
rm -r gdal/
```

Remove gdal target from 

```
vi CMakeLists.txt 
```

Then:

```bash
cd ../../build
cmake ../lidar-processing/install
make download
```

When running `make download`, if you see hash error, to download geoid, you need to substitute the correct hash strings:

```
vi /home/jyoung/opt/alps/build/share/share-geoid96-download.cmake
```

Then:

for geo96-as:

```
:%s/6b6aa5d82c3aeb3a91c2ab9a780f825f/d41d8cd98f00b204e9800998ecf8427e/g
```

for geo96-hw:

```
:%s/e3651b9301d469ee511c2edf6f6fdb18/d41d8cd98f00b204e9800998ecf8427e/g
```

for geo96nc:

```
:%s/5276e32d7c33a59ac0c6d52982181d39/d41d8cd98f00b204e9800998ecf8427e/g
```

for geo96nw:

```
:%s/906c16b315597b9d0a479ae4bb2f49a1/d41d8cd98f00b204e9800998ecf8427e/g
```

for geo96pr:

```
:%s/29b2c9c40156449483f24c876110f74e/d41d8cd98f00b204e9800998ecf8427e/g
```

for geo96se:

```
:%s/12ea932b252cd914ced4718919287d48/d41d8cd98f00b204e9800998ecf8427e/g
```

for geo96sw:

```
:%s/9090227d9e000467e3c1a281cfba4987/d41d8cd98f00b204e9800998ecf8427e/g
```

When running `make download`, if you see the following error:

```bash
-- MD5 hash of
    /home/jyoung/opt/alps/build/Download/tcl-tk/core-8-5-19.tar.gz
  does not match expected value
    expected: '905dd7d0c601202680887006095b58c6'
      actual: '5e03cbe2ffe8fe462fde22a08ebc7139'

```

Replace hash `905dd7d0c601202680887006095b58c6` in `/home/jyoung/opt/alps/build/Stamp/tcl-tk/download-tcl-tk.cmake` file with `5e03cbe2ffe8fe462fde22a08ebc7139` string, so the file is downloaded and extracted.

In vi, run 

```
:%s/905dd7d0c601202680887006095b58c6/5e03cbe2ffe8fe462fde22a08ebc7139/g
```

to replace old hashes with the expected hash.



Rerun:

```bash
make download
```

That should run with no errors.

Finally, run

```bash
make install
```



After installing ALPS in a user's home directory under `opt/alps`, all executables are in `opt/alps/lidar_processing/src`. Add the path to their bash profile so they can execute them from anywhere on Yeti.

```bash
vi ~/.bash_profile
```

Add the line:

```
PATH=$PATH:$HOME/opt/alps/bin
PATH=$PATH:$HOME/opt/alps/lidar-processing/src
```

Source:

```bash
source ~/.bash_profile
```

Now, the executable `alps` is available anywhere on Yeti.



#### To run the ALPS GUI on Yeti

Login to the viz node: <https://hub.cr.usgs.gov/docs/wiki/vizualizationServer/index.html>

Create a full desktop session, open up a Terminal (Applications - System Tools - Terminal).