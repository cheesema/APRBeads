# APRBeads

git clone --recursive #path_to_repo 

Then change the LibAPR repo to develop, should then work.


Installation
```
Cmake ..
make Example_get_par
```

Using the application
```
./Example_get_apr -i membrane_3a_gSFullMachinery_sEE_zStack.tif -d /Volumes/BevanT5/ImageData/Anastasia/ -o mem -I_th 1000 -min_signal 200 -i_rab5 Rab5_3a_gSFullMachinery_sEE_zStack.tif
```
