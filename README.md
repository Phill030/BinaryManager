# BinaryManager
## A binary reader/writer for the rust language, with a similar syntax to the C# BinaryWriter and BinaryReader
## Modified version of binary_rw which makes the stream public and add additional methods like read_bytes_at or read_big_string

------------------------------
#### Examples

Example code for reading

```rust
extern crate binary_rw;
use binary_rw::{
    filestream::{Filestream, OpenType},
    BinaryReader
};

fn main() {
  let mut fs = Filestream::new("test.bin", OpenType::Open).expect("Failed to open file"); 
  let mut binary_file = BinaryReader::new(&mut fs);

  let read_value = binary_file.read_f32().expect("Failed to read f32");
  println!("{:?}", read_value);
}
```

Example code for writing
```rust
extern crate binary_rs;
use binary_rs::{
    filestream::{Filestream, OpenType},
    BinaryReader
};

fn main() {
  let mut fs = Filestream::new("test.bin", OpenType::OpenAndCreate).expect("Failed to open file"); 
  let mut binary_file = BinaryWriter::new(&mut fs);
  
  let value: f32 = 30.5;
  binary_file.write_f32(value).expect("Failed to write f32");
}
```

#### TODO

