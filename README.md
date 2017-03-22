# addon

gcc -c -fPIC -Wno-attributes -w -D AMD64 -DMODULE_NAME=scripting_wrapper -std=c++11 -fpermissive -I/opt/node/include/node  -I/usr/include/nodejs/deps/v8/include/ -I/usr/include/nodejs/src/ -I/usr/include/python3.5/ -I/usr/local/lib64/R/include  -I/usr/local/lib64/R/library/Rcpp/include  -I/usr/local/lib64/R/library/RInside/include -I/usr/include addon.cpp 

gcc -pthread -shared  -L/usr/lib/python3.5/config-3.5m-x86_64-linux-gnu/ -L/usr/lib64 -L/usr/local/lib64/R/lib -lR -L/usr/local/lib64/R/lib -lRblas -L/usr/local/lib64/R/lib -lRlapack  -L/usr/local/lib64/R/library/RInside/lib -lRInside  -lpython3.5  -lR -lglpk  -Wl,-rpath,/usr/local/lib64/R/library/RInside/lib addon.o -o addon.node

NODE_PATH=. node test_addon.js 
