# BeeGFS parallel file system

## BeeGFS on Wynton
For storage, Wynton uses the BeeGFS file system.

BeeGFS is a parallel file system. This means the file system is spread across many different servers.

Our BeeGFS infrastructure as of September 2020 includes
- 6 metadata servers (SSD drives)
- 20 storage servers (HDD storage drives, SSD cache drives)
- 1 management server

## BeeGFS Services
Like many parallel file systems, BeeGFS provides different services for different types of file access:
- **storage service**
  - Stores the actual data
- **metadata service**
  - Provides information about files and directories, including the file permissions, ownership, and importantly, where the chunks that make up the file reside on the storage servers
- **management service**
  - Keeps track of all the available services and their status
- **client service**
  - Runs on the client to mount the filesystem and provide Linux access to the metadata and storage

### Advantages
  - Overall throughput can be huge.
  - Redundancy can be built in by mirroring services.
  - Adding new storage and/or metadata services is easy and requires no downtime.

### Caveats
  - From the perspective of an individual client node, performance is limited by the network bandwidth of that node.
  - Since all metadata requests also go over the network, network latency becomes extremeley important.
