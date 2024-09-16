---
type: checkpoint
date: 2024-09-19
title: 'Checkpoint 2: TCP Basics'
due_event: 
    type: due
    date: 2024-10-04T23:59:59+8:00
    description: 'Checkpoint #2 due'
---

# Introduction
In this checkpoint, you need to implement a basic TCP with:

* Sequence number and acknowledgement number, and
* Sliding window.

The starter code is provided for you which is a stop-and-wait plementation built on UDP. You need to implement the seq/ack numbering and sliding window based on it.

# Starter code
The two sample applications server.cc and client.cc are the same with those in checkpoint 1. 

The API exposed to applications is defined in foggy_tcp.h and consists of four core functions whose signatures should not be changed :```foggy_socket()```, ```foggy_close()```, ```foggy_read()```, and ```foggy_write()```. An application requests a new foggy-TCP socket by calling the foggy_socket function. 

While the functions defined in the API are implemented in foggy_tcp.cc, which runs on the same thread as the application, most of foggy-TCP’s core logic actually runs in a separate backend thread. This is important as TCP must
be able to work independently from the application (i.e., receiving, acknowledging and retransmitting packets). 

# Run the starter code
The started code is hosted in branch **cp2**. You may fetch this branch to your local machine.
```bash
git fetch cp2
git checkout cp2
```

Then build foggy-tcp
```bash
make foggy
```

In the server VM, at the `/vagrant/foggytcp` folder, run the server with the following command:
```bash
./server 10.0.1.1 3120 test.out
```

In the client VM, at the `/vagrant/foggytcp` folder, run the client with the following command:
```bash
./client 10.0.1.1 3120 src/client.cc
```

Now you have successfully transmitted the `client.cc` file from the client to the server, named as `test.out`.