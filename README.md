# Onion Monero Viewer

Currently, there is not possible to search for transactions in Monero Blockchain
online associated with a given address and viewkey. This is a serious problem,
especially for people using paper wallets, since they cant verying if they recived
founds whitch they expect.

In this example, this problem is address by development of an online hiden service
where users can input anonymouskt their address and viewkey to search for
associated transaction. The example not only shows how to use Monero C++ libraries,
 but also demonstrates how to use:

 - [crow](https://github.com/ipkn/crow) - C++ micro web framework
 - [lmdb++](https://github.com/bendiken/lmdbxx) - C++ wrapper for the LMDB
 - [mstch](https://github.com/no1msd/mstch) - C++ {{mustache}} templates
 - [rapidjson](https://github.com/miloyip/rapidjson) - C++ JSON parser/generator


## Onion address

Tor users:

 - [http://dont-know-yet.onion](http://dont-know-yet.onion.onion)

Non tor users, can try tor proxy, e.g.,

 - [http://dont-know-yet.onion](http://dont-know-yet.onion.onion.to)

## Still under development

The Onion Monero Viewer is still under development and testing.
So not everything can work as expected and the explorer can be offline from time
to time, when changes are being made to it.

## Onion Monero Viewer features

The key features of the Onion Monero Blockchain Explorer are

 - available as a hidden service,
 - no javascript, no web analytics trackers, no images,
 - open sourced,
 - made fully in C++,
 - the only explorer showing ring signatures,
 - the only explorer showing transaction extra field,
 - the only explorer that can show which outputs belong to the given Monero address and viewkey,
 - the only explorer showing detailed information about mixins, such as, mixins'
 age, timescale, mixin of mixins,
 - the only explorer showing number of amount output indices.

## Prerequisite

Everything here was done and tested using Monero 0.9.4 on Ubuntu 16.04 x86_64.

Instruction for Monero 0.9 compilation and Monero headers and libraries setup are
as shown here:
 - [Compile Monero 0.9 on Ubuntu 16.04 x64](https://github.com/moneroexamples/compile-monero-09-on-ubuntu-16-04)
 - [lmdbcpp-monero](https://github.com/moneroexamples/lmdbcpp-monero.git)

## C++ code

```c++

```

## Example screenshot

![Onion Monero Blockchain Explorer](https://raw.githubusercontent.com/moneroexamples/onion-monero-viewer/master/screenshot/screenshot.jpg)


## Compile and run the explorer

##### Monero headers and libraries setup

The Onion Explorer uses Monero C++ libraries and headers. Also some functionality
 in the Explorer for mempool is achieved through [patching](https://github.com/moneroexamples/compile-monero-09-on-ubuntu-16-04/blob/master/res/tx_blob_to_tx_info.patch)
 the Monero deamon.
 Instructions how to download Monero source files, apply a patch, compile  Monero,
 setup header and library files are presented here:

- https://github.com/moneroexamples/compile-monero-09-on-ubuntu-16-04 (Ubuntu 16.04)
- https://github.com/moneroexamples/compile-monero-09-on-arch-linux (Arch Linux)


##### Custom lmdb database (optional)

Most unique search abilities of the Onion Explorer are achieved through using
a [custom lmdb database](https://github.com/moneroexamples/lmdbcpp-monero.git) constructed based on the Monero blockchain.
The reason for the custom database is that Monero's own lmdb database has limited
search abilities. For example, its not possible to search for a tx having a
 given key image, except by performing an exhaustive search on the blockchain which is very time consuming.

Instruction how to compile the `lmdbcpp-monero` are provided here:

 - https://github.com/moneroexamples/lmdbcpp-monero.git

The custom database is rather big, 12GB now, and it must be running alongside Monero deamon
 so that it keeps updating itself with new information from new blocks as they are added
  to the blockchain.

For these reasons, its use is optional. However, without it, some searches wont be possible,
e.g., searching for key images, output and tx public keys, encrypted payments id.

##### Compile and run the explorer
Once the Monero is compiled and setup, the explorer can be downloaded and compiled
as follows:

```bash
# download the source code
git clone https://github.com/moneroexamples/onion-monero-viewer.git

# enter the downloaded sourced code folder
cd onion-monero-viewer

# create the makefile
cmake .

# compile
make
```

When compilation finishes executable `xmrviewer` should be created.

To run it:
```
./xmrviewer
```

Example output:

```bash
[mwo@arch onion-monero-viewer]$ ./xmrviewer
2016-May-28 10:04:49.160280 Blockchain initialized. last block: 1056761, d0.h0.m12.s47 time ago, current difficulty: 1517857750
(2016-05-28 02:04:49) [INFO    ] Crow/0.1 server is running, local port 8081
```

Go to your browser: http://127.0.0.1:8081


## Other examples

Other examples can be found on  [github](https://github.com/moneroexamples?tab=repositories).
Please know that some of the examples/repositories are not
finished and may not work as intended.

## How can you help?

Constructive criticism, code and website edits are always good. They can be made through github.

Some Monero are also welcome:
```
48daf1rG3hE1Txapcsxh6WXNe9MLNKtu7W7tKTivtSoVLHErYzvdcpea2nSTgGkz66RFP4GKVAsTV14v6G3oddBTHfxP6tU
```
