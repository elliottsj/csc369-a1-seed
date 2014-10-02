csc369-a1-seed
==============

Starter code & documentation for CSC369 Fall 2014, Assignment 1

## Overview

This repository contains the starter code and a slightly-modified `Makefile` for Assignment 1:

<http://www.cdf.toronto.edu/~csc369h/fall/assignments/a1/a1.html>

## Makefile

The `Makefile` is modified to compile a `test_malloc` binary *and* a `test_malloc_opt` binary
instead of just `test_malloc`.

## Usage

Initialize your project directory as a [`git-svn`][git-svn] repository:

    cd path/to/CSC369/
    git svn clone --username=g4name https://markus.cdf.toronto.edu/svn/csc369-2014-09/group_xxxx/a1
    cd a1/

(Replace `g4name` with your CDF name and `group_xxxx` with your own)

Pull this repository's contents:

    git pull https://github.com/elliottsj/csc369-a1-seed.git
    
Then commit it to your MarkUs Subversion repository:
    
    git svn dcommit

## Testing

To test your program, first compile the binaries:

    make

Then run it with the test traces:

    ./test_malloc short1.trace
    ./test_malloc random-4-10000-4096.trace

### Traces

The Python script `genrandom.py` generates "'traces' which are text files containing a series of malloc and free operations to perform":

    Usage: genrandom.py numthreads numblocks maxblocksize

The output of this script is formatted like this:

    m 0 0 2040
    m 0 1 2040
    f 0 1
    m 1 2 48
    m 1 3 4072
    f 1 3
    m 2 4 4072
    f 0 0
    f 1 2
    m 2 5 4072
    f 2 4
    f 2 5

The columns are:

- `m` or `f`: `m` calls `malloc()` while `f` calls `free()`
- Integer specifying the thread on which to allocate/free the block
- An index to identify the block
- If first column is `m`, the number of bytes to allocate

For example:

    m 1 3 4072

will allocate a 4072-byte block on thread 1 and give it an index of 3. The following operation will free this block:

    f 1 3

## Debugging

Simply use [CLion](http://www.jetbrains.com/clion/) to open `CMakeLists.txt`. 
Add a run configuration, specify the working directory and trace file argument, then click Debug.

[git-svn]: http://git-scm.com/book/en/Git-and-Other-Systems-Git-and-Subversion
