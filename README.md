# NewHope-Usenix

Implementations of the NewHope Ring-LWE-based key exchange as described
in the [USENIX Security 2016 paper *Post-quantum key exchange -- a new hope*](https://newhopecrypto.org/resources.shtml) by 
[Erdem Alkım](https://erdemalkim.github.io/),
[Léo Ducas](https://homepages.cwi.nl/~ducas/),
[Thomas Pöppelmann](http://tpoeppelmann.de), and
[Peter Schwabe](https://cryptojedi.org).

## Build instructions
To obtain and build the code, run the following sequence of commands:
```
 git clone https://github.com/newhopecrypto/newhope-usenix.git
 cd newhope-usenix/ref && make
 cd ../avx2 && make
 cd ../torref && make
 cd ../toravx2 && make
```
 This will build the binaries
* `ref/test/test_newhope`,
* `ref/test/test_statistical`,
* `ref/test/testvectors`,
* `ref/test/speed`,
* `avx2/test/test_newhope`,
* `avx2/test/test_statistical`,
* `avx2/test/testvectors`,
* `avx2/test/speed`,
* `torref/test/test_newhope`,
* `torref/test/test_statistical`,
* `torref/test/testvectors`,
* `torref/test/speed`,
* `toravx2/test/test_newhope`,
* `toravx2/test/test_statistical`,
* `toravx2/test/testvectors`, and
* `toravx2/test/speed`.

The `test_newhope` binary performs various key exchanges and outputs nothing if they are successful. 
The `test_statistical` generates many keys without final hashing and prints statistics on the distribution of ones and zeroes in those keys. 
The testvectors binary runs many key exchanges with deterministic "random-number" generation to ensure compatibility 
of independent implemtenations and the speed binary performs benchmarks and prints results.

The `torref` and `toravx2` implementations use a different, constant-time, generation of the polynomial a from a seed as described in the paper. 
The testvectors generated by those implementations are not compatible with the testvectors generated by `ref` and `avx2`.

Aside from the implementations of the key exchange, the software package also contains 5 Python scripts in the scripts
subdirectory. For details of those scripts please refer to the in the [paper](https://newhopecrypto.org/resources.shtml).

## License
All code in this repository is in the public domain.
For Keccak, ChaCha, and AES we are using public-domain
code from sources and by authors listed in 
comments on top of the respective files.
