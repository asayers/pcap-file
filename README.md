# pcap-file
A small crate providing everything you need to read and write pcap files in RUST.

Licensed under MIT.


### Documentation

https://docs.rs/pcap-file


### Installation

This crate is on [crates.io](https://crates.io/crates/pcap-file).
Add it to your `Cargo.toml`:

```toml
[dependencies]
pcap-file = "0.7.0"
```


### Example

```rust
use std::fs::File;
use pcap_file::{PcapReader, PcapWriter};

let file_in = File::open("test.pcap").expect("Error opening file");
let pcap_reader = PcapReader::new(file_in).unwrap();

let file_out = File::create("out.pcap").expect("Error creating file");
let mut pcap_writer = PcapWriter::new(file_out).unwrap();

// Read test.pcap
for pcap in pcap_reader {

    //Write each packet of test.pcap in out.pcap
    pcap_writer.write_packet(&pcap).unwrap();
}
```