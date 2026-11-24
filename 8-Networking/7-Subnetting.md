# Subnetting

**YouTube Playlist:** [You Suck at Subnetting](https://www.youtube.com/playlist?list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF)

**Article:** [Networking Basics: What is IPv4 Subnetting?](https://www.cbtnuggets.com/blog/technology/networking/networking-basics-what-is-ipv4-subnetting)

---

### Core Concept: What Is Subnetting?

**Subnetting** splits a larger IPv4 network into smaller networks (**subnets**) to reduce wasted public IPv4 addresses, contain broadcast/network traffic, strengthen security boundaries, and make networks easier to manage and scale.

---

### 1. IPv4 Structure & Binary Basics

* **32-bit addresses split into 4 octets:** Each octet has **8 bits** separated by dots (e.g., `192.168.1.20`), ranging from `0` to `255` (`11111111` in binary = $128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255$).
* **Maximum IPv4 value:** `255.255.255.255` (`11111111.11111111.11111111.11111111`).

---

### 2. Network Portion vs. Host Portion & CIDR Masks

* Every IP address has two parts:
* **Network portion:** Identifies the network/group (analogous to city/state/zip code).
* **Host portion:** Identifies individual devices on that network (analogous to house/street number).


* **Subnet masks & CIDR (`/prefix`):** Define how many of the 32 bits belong to the network (`1`s in a binary mask) versus hosts (`0`s in a binary mask).
* Example: `172.16.56.40` with `/24` (`255.255.255.0`) locks the first 24 bits (`172.16.56`) to the network and leaves 8 host bits for devices.
* Common baseline masks: `/8` (`255.0.0.0`), `/16` (`255.255.0.0`), and `/24` (`255.255.255.0`).



---

### 3. Legacy IP Address Classes (A, B, C)

Out of five IP classes, **Classes A, B, and C** are the ones used for standard subnetting:

| Class | Starting IP Range | Default Network Bits | Host Capacity |
| --- | --- | --- | --- |
| **Class A** | `1.0.0.0` – `127.0.0.0` | First octet (`/8`) | Most hosts (large enterprises) |
| **Class B** | `128.0.0.0` – `191.255.0.0` | First two octets (`/16`) | Medium host capacity |
| **Class C** | `192.0.0.0` – `223.255.255.0` | First three octets (`/24`) | Fewest hosts (common in home/small networks) |

Stealing ("borrowing") bits from the host side increases the number of subnets while reducing usable hosts per subnet.

---

### 4. Practical Walkthrough (`43.17.255.71/27`)

* `43.17.255.71` starts in the **Class A** range (default `/8`), but uses a **`/27`** mask (`32 - 27 = 5` host bits).
* In the final octet, `/27` creates **8 possible subnets** stepping in blocks of $2^5 = 32$ (`0`, `32`, `64`, `96`, `128`, `160`, `192`, `224`).
* Because `71` falls between `64` and `96`, the host lives in the **`43.17.255.64`** subnet.
* The article notes that while learning binary/block math is essential, router commands like `show ip route` on Cisco devices can also display connected subnet routes directly.

---

### Summary & Next Steps

* **Summary:** The article covers binary-to-decimal octets, network vs. host bits, CIDR masks, legacy A/B/C classes, and a `/27` subnet identification walkthrough.
* **Key Takeaways:**
* Subnetting trades host bits for more subnets (or vice versa) to avoid address waste and segment traffic.
* Knowing how to find the subnet boundary manually helps when you don't have router output in front of you.


* **Action Step:** Trace `43.17.255.71/27` in the last octet (`64` to `95` total block size of 32) to identify its network ID (`.64`), usable host range (`.65`–`.94`), and broadcast ID (`.95`).
* **Best Option / Recommendation:** Pair binary/CIDR boundary math with hands-on subnet practice so you can quickly spot which subnet an IP belongs to during troubleshooting or exams.
* **Alternatives:** Once IPv4 subnetting clicks, moving on to **IPv6 subnetting** and **NAT/routing tables** builds directly on the same network-versus-host boundary concepts.