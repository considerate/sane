# sane - Simple Array of Numbers Encoding

An array encoded in the `sane` format consists of
1. The ASCII-encoded byte sequence SANE (0x53 0x41 0x4E 0x45)
2. A little-endian uint32 encoding the length of the shape
3. A little-endian[^shape-endianness] shape as a sequence of little-endian uint64 sizes for each dimension
4. A uint8 specifying the data type
5. A little-endian uint64 encoding the byte length of the data of the array
6. A sequence of the numbers as specified by the data-type in row-major order (C-order)

[^shape-endianness]: A little-endian shape has the fastest-changing dimension first. For the C-expressions `A[i][j]`, the size of the dimension corresponding to `j` precedes the size of the dimension corresponding to `i`.

## Data Types

Supported data types are
- 0: float32
- 1: int32 (signed)
- 2: uint32 (unsigned)
- 3: float64
- 4: int64 (signed)
- 5: uint64 (unsigned)
- 6-255: reserved

All supported data types are stored in little-endian byte order.
