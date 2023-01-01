
# Compiling help in Linux: shared and static

## Flags for compiling
CFLAGS=

## Some basic examples
gcc -o func-a.o a.c b.c
gcc -o func-b.o func-b.c

# Creating and using libraries

## Static Libs: used in some cases, like the wrf-model. Some programs/libs need that the dependencies constructed with the same compiler.

https://tldp.org/HOWTO/Program-Library-HOWTO/static-libraries.html
ar -ru lib-funcs.a func-a.o func-b.o
Generate index
ranlib lib-funcs.a


## Shared Libs
https://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html

gcc -shared -Wl,-soname,your_soname \
    -o library_name file_list library_list

Here's an example, which creates two object files (a.o and b.o) and then creates a shared library that contains both of them. Note that this compilation includes debugging information (-g) and will generate warnings (-Wall), which aren't required for shared libraries but are recommended. The compilation generates object files (using -c), and includes the required -fPIC option:

gcc -fPIC -g -c -Wall a.c
gcc -fPIC -g -c -Wall b.c
gcc -shared -Wl,-soname,libmystuff.so.1 \
    -o libmystuff.so.1.0.1 a.o b.o -lc

https://www.intezer.com/blog/malware-analysis/executable-linkable-format-101-part-4-dynamic-linking/

LD_LIBRARY_PATH: environment variable: contains the path where the ld will search for libraries. It normalmente is used by user development. Problems:
- (Impact on For all program that is executed, the system will search here first for dependto the f.
- (Impact on security): as usually the dir included in LD_LIBRARY_PATH is writable by user, it can be abused by malware to write malicious libs.
