This is an implementation of the Google File System in Python, I have implemented simple GFS and incorporated some modifications, primarily using SWIM Protocol to deal with network faults and improve performance 
## Getting Started

Installation Instructions
### Use python version 3.8.0
`pip install -r requirements.txt`

``source GFS/bin/activate``

The implementation consists of a master, chunkserver, and gfs client implementation in the respective files. To run the implementation you must follow these steps:
1. Configure the GFS model in the `constants.py` file as follows:
   
   a. Choose the client's IP Address and TCP Port Number

   b. Choose the master's IP Address and TCP Port Number

   c. Make sure that port number TCP Port + 1000 is free (this is used for receiving heartbeats from chunkservers)

   d. Make lists of IP Addresses and TCP Port Numbers for chunkservers

   e. **Note**:  Number of chunkservers should be multiple of 3

   f. Make lists of IP Addresses and TCP Port for backup chunkservers

   g. **Note**: Make sure the all the port numbers in the TCP Ports list and TCP Port + 1000 remain free

   h. Start redis instances on x + 500 port where x is a TCP Port number used in `constants.py`. Make sure this is the case for master, client as well as all the chunkservers.
2. **How to start?**

   a. Start all the chunkservers as ``python3 chunkserver.py i``, where i is the chunkserver number which is getting started

   b. Start the master as ``python3 master.py``. Before the master starts make sure that all the chunkservers are running, otherwise master will miss the heartbeat of chunkservers which were suppose to be in running state and take the corresponding action.

   c. Start the client as ``python3 client.py``. # you can now use this client to read and write files. This is not an API and is just the architecture of how the client works. You can use this to write your own API.


---
