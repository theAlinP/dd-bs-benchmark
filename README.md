# dd-bs-benchmark

This is a project aiming to find the average read and write transfer speeds a device is able to achieve by running `dd` with various block sizes. Currently, block sizes from 512 bytes to 64 MiB are used (512, 1024, 2048, ... 65536, ... 67108864). That's 18 tests. It will help you find the optimal input and output block sizes to use with the respective device to achieve high transfer speeds.

## dd-ibs-benchmark.sh
`dd-ibs-benchmark.sh` creates a file in the given directory of the given size then reads it repeatedly with `dd` using different block sizes and print the read speeds achieved. You can then find the optimal __**input**__ block size(s) to use with the respective drive to achieve a high read speed.

### How to use
The script accepts 2 arguments: a folder path and a number.
```
./dd-ibs-benchmark.sh /path/to/directory [number]
```
The folder argument is mandatory and it should be a path to a directory on the drive. The second argument is optional and it is the size in bytes of the temporary file that will be created in the provided folder. It should be a natural number a.k.a. positive integer in the form [0-9], like 1234 but not +1234 or -1234 or 12.34 nor 1,234. If one is not provided, 268435456 bytes (256 MiB) will be used by default. 256 MiB are enough for something like a flash drive or a memory card which are relatively slow but if you want to benchmark a faster Hard Drive or worse, a Solid State Drive you would need to use a larger file because 256 MiB would be read or written in less than a second, which could give unreliable results.

For example:
```
./dd-ibs-benchmark.sh /media/user/External_storage 536870912
```
The command above will create a 512 MiB file with `dd` in /media/user/External_storage then read it back repeatedly with `dd` using different block sizes and print the read speeds recorded. If no size were specified, the script would create a 256 MiB file.

## License
This software is licensed under the MIT License (MIT Expat License). The full text can be found in the file LICENSE.
