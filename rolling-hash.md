# Rolling Hash Algorithm in Rust

_Spec v1 (2019-09-27)_

Make a rolling hash based file diffing algorithm in Rust, that splits any file it's given into hashed chunks. When compared with a different file or a different version of the same file, it gives the exact chunk(s) that have changed. For example, in a distributed file storage system this enables much smaller file deltas to be updated over a network, or locally, a version control system that only saves the delta of each version.


## Requirements

- Work with byte data. Demonstrate the functionality with text by converting it to bytes before diffing and vice versa.
- Hashing function gets the data as a parameter. Separate possible filesystem operations.
- Working tests, > 85 % coverage preferred
- Chunk size can be fixed or dynamic, but must be split to at least two chunks on any sufficiently sized data.
- Well-written unit tests function well in describing the operation, no UI necessary.
