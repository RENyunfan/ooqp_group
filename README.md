# OOQP

# 0 Install gfortran

```bash
sudo apt-get install gfortran
```



# 1 Install blas

```bash
cd blas-3.8.0/BLAS-3.8.0/
gfortran -O3 -c *.f
ar cr libblas.a *.o
sudo cp ./*.a /usr/lib 
```

# 2 Install LAPack

```bash
cd lapack-3.9.0 

make  -j7
# Then the build may failed: Makefile:463: recipe for target 'znep.out' failed
# You may need try block below a few times until it success.
# BEGIN
ulimit -s 100000
make clean 
make -j7
#END

sudo cp ./liblapack.a /usr/local/lib/
```

If you meet error, see https://unix.stackexchange.com/questions/428394/lapack-make-fails-recipe-for-target-znep-out-failed-error

# 3 MA27

```bash
./configure
make
sudo make install

```

# 4 OOQP

```bash
cd OOQP
./configure
make
sudo make install
```

The terminal output may not look so normal, don’t be nervous, if you see line below after `sudo make install`, the OOQP is successfully installed.

```bash
➜  OOQP sudo make install
/usr/bin/install -c -d /usr/local/include/ooqp	
/usr/bin/install -c ./include/*.h /usr/local/include/ooqp
/usr/bin/install -c -d /usr/local/lib
/usr/bin/install -c ./lib/*.a /usr/local/lib
if [ -d doc-src ]; then cd doc-src; fi; make
make[1]: Entering directory '/home/yunfan/Libs/ooqp_group/OOQP/doc-src'
cp -f ooqp-userguide/ooqp-userguide.pdf ../doc/ooqp-userguide.pdf
pod2text distribution-docs/README.pod > ../README
pod2text distribution-docs/INSTALL.pod > ../INSTALL
pod2text distribution-docs/README_Matlab.pod > ../README_Matlab
pod2text distribution-docs/README_Windows.pod > ../README_Windows
pod2text distribution-docs/COPYRIGHT.pod > ../COPYRIGHT
doxygen
make[1]: doxygen: Command not found
GNUmakefile:38: recipe for target 'reference_manual' failed
make[1]: *** [reference_manual] Error 127
make[1]: Leaving directory '/home/yunfan/Libs/ooqp_group/OOQP/doc-src'
GNUmakefile:102: recipe for target 'install_docs' failed
make: *** [install_docs] Error 2
```

