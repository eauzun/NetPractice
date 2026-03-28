*This project has been created as part of the 42 curriculum by emuzun.*

# NetPractice

## Description

NetPractice is a networking exercise built around one question: given a broken network, what needs to change to make it work?

There is no code to write. The project is a series of 10 configurations — each one a small network diagram with missing or incorrect values. The goal is to fill them in correctly so that every device can reach every other device it's supposed to reach.

The concepts involved are the fundamentals of IP networking. An IP address is a 32-bit number split into a network part and a host part — the subnet mask determines where that boundary is. ANDing an address with its mask gives the network address; the highest address in that range is the broadcast address, and everything in between is usable by hosts. CIDR notation (`/24`, `/28`, etc.) is just a shorthand for the mask — the prefix length tells you how many bits belong to the network side, which directly determines how many hosts fit in that subnet.

Routers connect subnets together. Each router interface belongs to exactly one subnet. When a host needs to reach an address outside its own subnet, it sends the packet to its default gateway — a router interface on the same subnet. The router then consults its routing table: each entry maps a destination network to a next hop. If no specific route matches, the default route (`0.0.0.0/0`) catches the rest.

Get any of this wrong — overlapping subnets, a gateway that isn't in the same subnet as the host, a missing route — and traffic goes nowhere. Get it right and the diagram lights up green.

---

## Instructions

### Running the Interface

1. Go to the project page and download `net_practice.1.9.tgz`
2. Extract the archive
3. Open `index.html` — either from the terminal:

```bash
open index.html
```

or by double-clicking it in your file manager.

### Solving & Exporting

Each level must be solved individually. Once a configuration is correct, click **"Get my config"** on the page — this exports the solution as a `.json` file. All exported files must be placed in the root of the repository, one per level.

### Submission

Push all 10 `.json` configuration files to the root of your Git repository. There is no binary to compile or script to run — the `.json` files are the submission.

---

## Resources

- [Subnet Calculator](https://www.subnet-calculator.com/)
- [CIDR to IPv4 Conversion — ipaddressguide.com](https://www.ipaddressguide.com/cidr)
- [TCP/IP Addressing and Subnetting — Cisco](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html)
- [OSI Model Explained — Cloudflare](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)

### Networking Concepts Covered

This project touches the following concepts:

- **TCP/IP addressing** — how 32-bit IPv4 addresses are structured and written in dotted-decimal notation
- **Subnet masks & CIDR** — how the prefix length defines the network/host boundary, and how to calculate network address, broadcast address, and usable host range
- **Subnetting** — splitting an address space into non-overlapping subnets sized to fit a given number of hosts
- **Default gateways** — how a host forwards traffic destined outside its subnet
- **Routers & routing tables** — how routers match destination addresses to next hops, and the role of the default route (`0.0.0.0/0`)
- **Switches** — layer 2 devices that connect hosts within the same subnet without affecting IP routing

### AI Usage

We used AI for one part of the project.

**CIDR notation** — understanding how prefix lengths map to subnet masks, how to calculate the usable host range from a given prefix, and how to pick a prefix that fits a required number of hosts without overlap.

We used it to work through the math. The configurations are ours.