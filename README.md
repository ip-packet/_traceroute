# _traceroute

A minimal command-line utility to trace the path packets take to reach a specified network destination. It sends packets with increasing time-to-live (TTL) values, displaying each hop along the route—similar to the standard `traceroute` tool.

---

## Table of Contents

- [Features](#features)
- [Usage](#usage)
- [Example Output](#example-output)
- [Installation](#installation)
- [Requirements](#requirements)
- [Contributing](#contributing)
- [Contact](#contact)

---

## Features

- Maps the network path to a target host (domain name or IP address)
- Displays each hop with IP, hostname (if resolvable), and round-trip time
- Supports custom network interface and timeout
- Simple, minimal, and fast
- Linux support

---

## Usage

```
./_traceroute DESTINATION [-i=INTERFACE] [-t=TIMEOUT]

  DESTINATION : domain name or IPv4 address of the target host
  -i          : (optional) network interface to use (default: enp0s3)
  -t          : (optional) network response timeout in seconds (default: 3)
```

---

## Example Output

```
$ ./_traceroute 1337.ma
_TRACing ROUTE to 1337.ma (104.18.32.248)
 ,  from enp0s3 (10.13.100.30)
 1  10.13.254.254 [10.13.254.254] 0.674 ms
 2  10.21.1.1 [nat.1337.ma] 0.284 ms
 3  197.230.30.145 [197.230.30.145] 0.310 ms
 4  10.43.88.105 [10.43.88.105] 2.293 ms
 ...
 8  104.18.32.248 [104.18.32.248] 19.936 ms
```

Supports long routes and handles timeouts/missing hosts:

```
$ ./_traceroute 162.252.205.130
TRC_route to 162.252.205.130 (162.252.205.130)
 ,  from enp0s3 (10.13.100.30)
 1  10.13.254.254 [10.13.254.254] 0.808 ms
 2  10.21.1.1 [nat.1337.ma] 0.376 ms
 ...
39  #  130.117.14.46 [centurylink.mad05.atlas.cogentco.com] 0.052 ms
...
44  162.252.205.130 [bad.horse] 0.027 ms
```

---

## Installation

1. Clone this repository:
   ```sh
   git clone https://github.com/ip-packet/_traceroute.git
   cd _traceroute
   ```
2. Build the binary (example for C):
   ```sh
   make
   ```
   _(Or follow language-specific build instructions if provided.)_

3. Run as root (required for raw socket operations):
   ```sh
   sudo ./_traceroute <DESTINATION>
   ```

---

## Requirements

- Linux
- Root privileges (required for sending raw network packets)
- A C compiler and `make` (if building from source)

---

## Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

---

## Contact

For questions or support, please open an issue in this repository.

