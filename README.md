eigenmvn
========

### Multivariate Normal distribution sampling using C++11 and Eigen matrices.                                                                                   
This is taken from http://stackoverflow.com/questions/16361226/error-while-creating-object-from-templated-class           (also see http://lost-found-wandering.blogspot.fr/2011/05/sampling-from-multivariate-normal-in-c.html)                                                      

I have been unable to contact the original author, and I've performed the following modifications to the original code:                                                                                                           
 * removal of the dependency to Boost, in favor of straight C++11;                                                                                           
 * ability to choose from Solver or Cholesky decomposition (supposedly faster);                                                                              
 * fixed Cholesky by using LLT decomposition instead of LDLT that was not yielding a correctly rotated variance. See this link for more details: http://stats.stackexchange.com/questions/48749/how-to-sample-from-a-multivariate-normal-given-the-pt-ldlt-p-decomposition-o

 * turned matrix fixed sizes into dynamic sizes.
 
#### Usage
Compile the test exe with
```
g++ -I/usr/include -I/usr/include/eigen3 -g -std=c++11 test_eigenmvn.cc -o te
```
run with 
```
./te
```
Look at results with gnuplot:
```
gnuplot
plot 'samples_solver.txt', 'samples_cholesky.txt'
```

![alt text](/te.png "title")
