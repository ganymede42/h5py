Changes done by Thierry
=======================

Build
-----
```
git checkout psi2.5
git clean -xdf
mkdir -p /tmp/lib/python2.7/site-packages/
./setup.py configure --hdf5=../WorkBench/hdf5
./setup.py install  --prefix=/tmp
```


Update from official branch
---------------------------

```
./c2py.py -v --hdfDir=../WorkBench/hdf5/include --header=hdf5py.h --outFile=c2pyOut.txt gen

bcompare h5py/new.api_functions.txt h5py/api_functions.txt
check the files:
 - c2pyOut.txt
 - h5py/new.api_functions.txt
 - h5py/unused.api_functions.txt
 - h5py/new.api_types_hdf5.pxd
 - h5py/unused.api_types_hdf5.pxd

-> api_functions.txt:
   - update/clean signature (compare with h5py/new.api_functions.txt, h5py/unused.api_functions.txt)
   - add line: herr_t    H5DOwrite_chunk(hid_t dset_id, hid_t dxpl_id, uint32_t filters, const hsize_t *offset, size_t data_size, const void *buf)

-> api_types_hdf5.pxd:
   - optional update/clean (compare with  h5py/new.api_types_hdf5.pxd h5py/unused.api_types_hdf5.pxd)

-> h5py/h5d.pyx:
   - add def write_chunk(self...) function

-> h5py/h5p.pyx:
   - small fix

-> h5py/h5p.pyx:
   - small fix

```

Git Stuff
---------

```
git branch psi2.5
git tag psi2.5.0-1 -m 'PSI branch with chunk write'
git push ganymede42 psi2.5 psi2.5.0-1
```
