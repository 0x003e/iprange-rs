# iprange-rs

[![Crates Version](https://img.shields.io/crates/v/iprange.svg)](https://crates.io/crates/iprange)
[![Build Status](https://travis-ci.org/sticnarf/iprange-rs.svg?branch=master)](https://travis-ci.org/sticnarf/iprange-rs)

`iprange` is a Rust library for managing IP ranges. 

It provides fast adding and removing operations.

It also provides `merge`, `intersect` and `exclude` methods 
that enable you to manipulate it like a set.

Of course, you can test whether an IP address is in an `IpRange`.

**See the [documentation](https://docs.rs/iprange/) for details.**

## Example

```rust
extern crate iprange;
extern crate ipnet;

use std::net::Ipv4Addr;
use iprange::IpRange;
use ipnet::Ipv4Net;

fn main() {
    let ip_range: IpRange<Ipv4Net> = ["10.0.0.0/8", "172.16.0.0/16", "192.168.1.0/24"]
        .iter()
        .map(|s| s.parse().unwrap())
        .collect();

    assert!(ip_range.contains(&"172.16.32.1".parse::<Ipv4Addr>().unwrap()));
    assert!(ip_range.contains(&"192.168.1.1".parse::<Ipv4Addr>().unwrap()));
}
```

## License

`iprange` is licensed under the MIT license.