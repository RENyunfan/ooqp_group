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

modify

```
#lib: lapacklib tmglib
lib: blaslib variants lapacklib tmglib
```



```bash
cd lapack-3.9.0 
ulimit -s unlimited
sudo make -j8
cd INSTALL   

sudo cp ./liblapack.a /usr/local/lib/
```



# 3 MA27

```bash
./configure
make
sudo make install

```



# 4OOQP

```bash
cd OOQP
sudo chmod +x ./configure 

```

