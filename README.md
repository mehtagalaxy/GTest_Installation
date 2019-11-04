# GTest_Installation

Below are the steps to integrate Google test and Google Mock framework with CU code.

1.	Download Google test release-1.8,0 
cd 5G_CU; mkdir gt_ut ; cd gt_ut ;
wget https://github.com/google/googletest/archive/release-1.8.0.tar.gz
tar -xzvf googletest-release-1.8.0.tar.gz
cd googletest-release-1.8.0
mkdir mybuild
cd mybuild
2.	Compile google test code and generate a library.
g++ -std=c++11 -isystem ../googletest/include/ -I ../googletest/ -isystem ../googlemock/include/ -I ../googlemock/  -pthread -c ../googletest/src/gtest-all.cc
3.	Compile google mock code and generate a library.
g++ -std=c++11 -isystem ../googlemock/include/ -I ../googlemock/ -isystem ../googletest/include/ -I ../googletest/  -pthread -c ../googlemock/src/gmock-all.cc
4.	Link both library into one library for simplicity (say libgtest.a).
ar -rv libgtest.a gtest-all.o gmock-all.o
5.	Link this libgtest.a with CU library under test for the module being tested.
6.	Write test cases as per Google test provided framework. Add as many assertions and comparisons in test case output parameters.
7.	Run single test case, a group of testcases or all testcases as per requirement.
 
