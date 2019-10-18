supper_make

Getting Started
This Project Provide a Super Makefile which can easily to build the static library, shared library and the executable in all Unix Like OS

Prerequisites
1) Copy the common.mk to the project root folder
2) Create a Makefile in the root folder with two line:
export PROJECT_HOME:=$(shell pwd|sed "s/\/$$//g;")
include $(PROJECT_HOME)/common.mk


Make a Static Library Makefile
TYPE:=STATIC
include $(PROJECT_HOME)/common.mk

Make a Shared Library Makefile
TYPE:=SHARE
DEPS:=static_example
include $(PROJECT_HOME)/common.mk
#DEPS means depends on the statci_example module

Make a Executable Makefile
TYPE:=EXE
DEPS:=dynamic_example
include $(PROJECT_HOME)/common.mk
#DEPS dynamic_example, and dynamic_example depends static_example, so this object will auto depends static_example

Make a Target depends on System package Makefile
TYPE:=SHARE
DEP_PKGS:=python3
SHARE_SUBFFIX:=.so
LIB_PREFIX:=""
include $(PROJECT_HOME)/common.mk
#DEP_PKGS:=python3 is a system package which has a package file in xxxx/pkgconfig/python3.pc
#SHARE_SUBFFIX:=.so force the subffix to so (in mac book is the default is dylib)
#LIB_PREFIX:="" force the prefix to nothing, default is lib 
#after make the library, copy the ../example_build/example/lib64/third_party_example.so.0 to xxx/lib/python3.x/site-packages/
#so can test the python package using 
#python3 py_example.py

Make Targets Paths
#If make in Project XXX folder,
#the Targets path will like
../XXX_build
../XXX_build/XXX
../XXX_build/XXX/bin
../XXX_build/XXX/lib

Compatibility
All Unix and Linux Like platform

Authors
AU Gwok Dung David:
Email: kingbirdogd@gmail.com
Linkedin: https://www.linkedin.com/in/david-au-15632561/

License
This project is licensed under the BSD License
