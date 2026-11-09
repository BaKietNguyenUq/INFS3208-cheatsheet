# Cloud

## Def

Cloud computing is a specialised form of distributed computing that introduces utilisation models for remotely provisioning scalable and measured resources

### Characteristics

- On demand usage
- measured usage
- Multinency
- Resiliency
- Elasticity

## Business driver

- Capacity Planning (CP)
- Cost Reduction
- Organisational Agility

## Cloud vs Internet

- Cloud has a clear and finite boundary
- Cloud is usually private and offers metered IT resources
- Cloud often provides back-end processing capabilities

## Technology Innovations

### Clustering

- Group of independent IT resources that are interconnected and work as a single system.
- Cluster nodes have reasonably identical hardware and OS
- Cluster nodes are connected through dedicated, high-speed communication links.

### Grid Computing

- GC provides a platform in which computing resources are organized into one or more logical pools.
- These pools are collectively coordinated to provide a high-performance distributed grid (super virtual computer).

### Comapare to Cluster Nodes

- grid systems are much more loosely coupled and distributed.
- grid computing systems are often connected through a relatively low-speed network (e.g. Internet)

### Virtualisation

- VT is used to create virtual instances of IT resources.
- A layer of virtualization software allows physical IT resources to provide multiple virtual images of
  themselves
- Underlying processing capabilities that can be shared by multiple users.

### Scaling methods

- Horizontal scaling: allocating or releasing of IT resources (same
  type)

- Vertical scaling: higher or lower capacity of the current IT
  resources (less common due to downtime)

| Horizontal Scaling  | Vertical Scaling                   |
| ------------------- | ---------------------------------- |
| Add more servers    | Upgrade CPU/RAM of existing server |
| Scale out/in        | Scale up/down                      |
| Usually no downtime | May require downtime               |
| More flexible       | Limited by hardware                |

## Cloud delvery model

| Model    | Characteristics                                                                               | Examples                       |
| -------- | --------------------------------------------------------------------------------------------- | ------------------------------ |
| **IaaS** | Provides virtual machines, storage, and networking. Users manage OS and applications.         | AWS EC2, Google Compute Engine |
| **PaaS** | Provides a platform to develop and deploy applications without managing infrastructure or OS. | Google App Engine, Heroku      |
| **SaaS** | Provides ready-to-use applications over the internet. Users only use the software.            | Gmail, Google Docs             |

## Cloud deloyment model

- Public cloud: GCP, AWS

- Private cloud; UQCLoud

- Community cloud: Cloud for multi department in a company

- Hybrid cloud: private cloud (sensitive data) + public cloud (less sensitive cloud services)

## Cloud-Enabling Technology: technologies that make cloud computing possible.

- Broadband Networks and Internet Architecture
- Virtualisation Technology (VT)
- Data Centre Technology
- Web Technology
- Multitenant Technology

## Pros

- Reduced Investments and Proportional Costs
- Increased Scalability
- Increased Availability and Reliability

# VPC Network, Load Balancing & Cloud Architectures

A virtual private cloud (VPC) is a virtualized private cloud within a public cloud (GCP, AWS) for an organization

## Advantages of VPC:

- Better Security + All benefits of public cloud

## The key technologies for isolating a VPC from the rest of the public cloud are:

- Subnet: A subnet is reserved (not available to everyone) within the network - for private use.
- VPN: uses encryption to create a private network.
- VLAN: is a virtual LAN and it’s used to partition a network.
- NAT: NAT matches private IP addresses to a public IP address for connections with the public Internet.

## Regions and Zones

Cloud Providers organise IT resources by regions and zones.

- Availability Regions:
  - the geographic locations of the data centres
  - E.g, China, North America, Southeast Asia, East Asia, Europe, Middle East, etc

- Availability Zones - one or more discrete data centres with redundancy in a
  Region (independent zones lead to resilience) - Multiple zones are interconnected with encryption

## VPC and Subnets in GCP and AWS

- GCP:
  - A VPC network is a global resource; Subnets are regional resources.
  - Resources in different regions can belong to the same VPC network.
  - Routing and firewall rules are associated with the global VPC network.
- AWS:
  - A VPC is regional
  - A subnet is scoped to one Availability Zone
  - Each subnet must be associated with a route table; Subnets within the same
  - VPC can communicate through the VPC local route, subject to route tables,

## Load Balancing

- Load balancing improves the distribution of workloads across multiple
  computing resources, such as computers, a computer
  cluster, network links, central processing units, or disk drives.

- Load balancing aims to optimize resource use, maximize throughput,
  minimize response time, and avoid overload of any single resource.

- Using multiple components with load balancing instead of a single
  component may increase reliability and availability
  through redundancy.

- Load balancing load balancers can operate at different layers of the
  OSI stack (Layer 4 vs. Layer 7) and can be implemented via hardware
  appliances or software.

### Load Balancing algorithm

- Round Robin: Distributes requests equally between servers, regardless of their capacity.
- Weighted Round Robin: Distributes more requests to servers with higher capacity.
- Least Connections: Sends requests to the server with the fewest active connections.
- Random: Distributes requests randomly.

## Layer 4 LB vs Layer 7 LB

| Feature              | Layer 4 (Transport)         | Layer 7 (Application)       |
| -------------------- | --------------------------- | --------------------------- |
| **OSI layer**        | Transport layer             | Application layer           |
| **Protocols**        | TCP, UDP                    | HTTP, HTTPS, gRPC           |
| **Routing based on** | IP address, port            | URL, path, headers, cookies |
| **TLS/SSL**          | Usually passes through      | Can decrypt and inspect     |
| **Performance**      | Faster, lower overhead      | Slower, more flexible       |
| **Visibility**       | Cannot inspect HTTP content | Can inspect HTTP content    |
| **Examples**         | AWS NLB                     | AWS ALB                     |

# Container, Docker Commands, and Dockerfile

- Containers offer a logical packaging mechanism in which applications can be abstracted from the environment in which they actually run.

- Deploy container-based applications more easily and consistently than running VMs

## Pros

- Run Anywhere: Containers are able to run virtually anywhere, greatly easing development and deployment:
- Isolation: Containers virtualise hardware at the OS-level with a sandboxed view of the OS logically isolated from other applications.

## Linux Namespaces and Cgroups

- Namespaces are a feature of the Linux kernel that partition kernel resources such that one set of
  processes sees one set of resources, while another set of processes sees a different set. (Resourcoes isolation and parition)

- Control Groups (cgroups) are a Linux kernel feature that limits, accounts for, and isolates the resource usage (CPU, memory, disk I/O, network, etc.) of a collection of processes. (Resources limit and control)

## Images and container

### Images

- Contains
  - OS filesystem
  - configurations, metadata or manifest
  - One or more application
- An image is a read-only template with instructions for creating a Docker
  container.
- Docker images are stored in a Docker registry

### Container

- an instance created from an image, with runtime configuration and a writable layer.

## Dockerfile

- Dockerfile is a text file that defines the environment inside the container
- Dockerfile is a collection of instructions and commands (blueprint) and clearly tells what are contained in the image.

## Docker compose

## Docker swarm

- Docker Swarm manages a cluster of Docker nodes and schedules containers
- Docker Swarm is an orchestration tool
- A tool from Docker to work with distributed deployments of containers
- A cluster of Docker hosts

## Docker Machines

- Docker Machine allows you to provision Docker machines in a variety of environments.

## Raft Consensus Algorithm

- In a distributed system (like a Docker Swarm cluster), multiple computers need to agree on a shared state, even if some of them fail.

- A consensus algorithm is used to achieve this agreement.

### Why Does Docker Swarm Need It?

- Docker Swarm's manager nodes are responsible for the entire cluster's state.
- All manager nodes must have the exact same information

### States of Raff Algorithm

- Follower: Waits for instructions. All nodes start as followers.
- Candidate: Tries to become the leader.
- Leader: The single, active manager of the cluster.

## Container vs VMs

| Feature            | Containers                       | Virtual Machines                       |
| ------------------ | -------------------------------- | -------------------------------------- |
| **Isolation**      | Process-level (shared kernel)    | Full OS isolation (separate kernel)    |
| **Resource Usage** | High, share with OS host         | Heavy, each VM run full OS             |
| **Storage**        | Layered file system              | Require disk space to store            |
| **Startup Time**   | Fast (seconds)                   | Slower (seconds to minutes)            |
| **Performance**    | Near-native                      | Some virtualization overhead           |
| **Portability**    | High                             | Lower                                  |
| **Security**       | Weaker isolation (shared kernel) | Higher, isolated with OS kernels       |
| **Scalability**    | Easy and fast                    | Slower, resource-intensive             |
| **Use Cases**      | Microservices, CI/CD             | Legacy apps, different OS environments |
| **Tools**          | Docker, Kubernetes               | VMware, VirtualBox                     |

# Kubernetes

- k8s is an open-source container-orchestration system.
- k8s provides
  - Automated deployment,
  - Scaling and management of containerised applications.

## K8s Framwork

| Number | Component          | Label | Function                                                  |
| ------ | ------------------ | ----- | --------------------------------------------------------- |
| **1**  | etcd               | **F** | Stores all cluster data (key-value store).                |
| **2**  | api server         | **C** | Validates and configures Kubernetes API objects.          |
| **3**  | scheduler          | **B** | Assigns newly created Pods to Worker Nodes.               |
| **4**  | controller-manager | **E** | Runs control loops to maintain the desired cluster state. |

| Number | Component         | Label | Function                                     |
| ------ | ----------------- | ----- | -------------------------------------------- |
| **5**  | kubelet           | **A** | Ensures containers are running in Pods.      |
| **6**  | kube-proxy        | **G** | Maintains network rules on nodes.            |
| **7**  | Container Runtime | **D** | Software responsible for running containers. |

## K8s concepts and components

### Services

- ClusterIP (default): expose the port only inside the cluster
- NodePort: expose the target port on every node to the outside
- LoadBalancer: Uses an external load balancer to expose the service and distribute traffic.

### Control Plane (Master Node)

- Manages the (worker) nodes
  - Schedule (pod),
  - detect or respond to cluster events
- Provides User Interface
- FOUR processes need to run in Control Plane:
  - API Server, Scheduler, Controller Manager, Etcd

### Worker Nodes (Slave Nodes)

- Conduct actual works with multiple pods
- THREE processes need to run on every node
  - Container runtime, Kubelet, Kube proxy

## Reconciliation Loop

- Reconciliation Loop ensures that the system’s actual state always matches the user’s desired state
  .By continuously detecting and correcting differences

### How loop work

- Observe – Check what’s running now.
- Compare – See if it matches the YAML config.
- Act – Fix differences (e.g., start or stop pods).

## Kubernetes Objects

### Pods

- Contains one or more containers.
- Runs containers.
- the smallest deployable units of computing that you can create
  and manage in Kubernetes. It has a group of one or more
  containers, with shared storage and network resources.

### ReplicaSet

- Maintains the required number of Pods.

### Deployment

- Manages ReplicaSets
- Provides declarative updates to Pods and ReplicaSets.

### Services

- Provide a way to expose an app running on a set of pods as a networking services.
- Types of Services:
  - ClusterIP (default): Internal Service IP
  - NodePort: Exposes Service on a port of each node
  - LoadBalancer: External load balancer

### Ingress (DNS)

- manages external access to the services in a cluster, typically HTTP.

### ConfigMap

- Used to store non-confidential data in key-value pairs

### Secret

- Similar to ConfigMap, but is used to store secret data (user name, password, tokens, keys, etc)

### Persistent Volume

-     Provides persistent storage for applications.
- how you map external storage onto the cluster; resource

### Persistent Volume Claim

- a request for storage by a user; claim checks to the
  resource

### StatefulSet:

- manages stateful applications (e.g. SQL & NoSQL)
- deploys and scales a set of Pods (DBs)
- Maintains stable Pod identities.

# Vector Databases

A vector database is any database that allows you to store, index, and query vector
embeddings, or numerical representations of unstructured data, such as text, images,
or audio.

## Technologies

- Vector Embedding
- Similarity Search
- Indexing

## Database Partition

- Vertical Parition: Each partition store a subset of fields in data store
- Horizontal Parition: Each partition is a seperate data store

## Pros

- Data perspective
  - Support complex data
  - Embedding unstructured data (80% of the world's data is unstructured)
  - High-dimensional data handling
- Method perspective
  - Efficient and accurate similarity search and retrieval
  - Sophisticated query capabilities
- Application perspective
  - AI and machine learning integration
  - Scalability for modern applications

## Vector database Indexing

### Flat Index (Brute Force)

- a direct representation of the vector embedding
- Deliver the best accuracy but slow
- Search is exhaustive

### Used when

- Low-dimensional data
- Small-Scale Databases
- Simple Querying
- Real-time Data Ingestion
- Low Query Volume
- Benchmarking Comparisons

### Inverted File Product Quantization Index

- Lossy compression technique for high-dimensional vectors.
- How to do
  - takes the original vector, breaks it into smaller chunks
  - simplifies the representation of each chunk by creating a representative “code” for each chunk.
  - puts all the chunks back together

#### Traning codebook

Training - we build a “codebook” for each chunk.

1. An inverted file index is constructed: dividing the set
   of vectors into k Voronoi partitions. (reduce the search space)

2. Inside each Voronoi partition, each vector subtracted the coordinates of its centroid vector.

3. The product quantization algorithm is run on vectors from all the partitions:

- a. Splitting high-dimensional vectors into smaller subvectors.
- b. Quantizing these sub-vectors into a finite number of clusters or bins, each represented by a
  centroid.
- c. Using a codebook for each sub-vector to enable efficient storage and approximate distance calculation.

#### Inference

1. Find k nearest centroids of Voronoi partitions.
2. Calculate the query residual separately for k Voronoi partitions
3. The query residual is then split into subvectors.
4. Calculate the partial distance to each partition
5. Partial distances are summed up.
6. Maintaining a MaxHeap data structure for sorting
   the results. (Store n smallest structure at each step)

## Types of Vector Databases

### In-memory vector database (RedisAI, Torchserve)

- Store vectors directly in memory
- Enable fast read-and-write operations

### Disk-based vector database (Annoy, Milvus, ScanNN)

- Store vectors on disk
- Suitable for large data sets
- Using indexing and compression techniques

### Distributed vector database (FAISS, Elastics Search With Vector Plugin, Dask-ML)

- Spread vector data across multiple nodes or servers
- Allows for horizontal scalability and fault tolerance
- Suitable for managing massive data sets and high-throughput tasks

### Graph-based vector database (Neo4j, TigerGraph, Amazon Neptune)

- Model data as a graph
- Nodes and edges represent vector attributes or embeddings
- Excel at capturing complex relationships

### Time-series vector database (InfluxDB, TimescaleDB, Prometheus)

- Represent data collected over time as vectors

## Retrieval Augmented Generation

RAG is a method that combines retrieval-based models with generative models to enhance the
generation of contextually relevant and accurate responses.

### Generalized RAG Approach

- User sends query
- App forwards queries
- RAG retrieves + generates response
- LLM returns response

# NoSQL

- NoSQL databases are non-relational, purpose-built data systems optimised for a specific
  access pattern rather than for a general-purpose relational model.

- NoSQL databases typically favour flexible data models, horizontal scale-out, distributed
  deployment, low latency and high availability

## Types of NoSQL Databases

- Key-value stores
  - Key is a string while value can be in different types
  - Examples: Redis, Riak, Memcached, etc.

- Document stores
  - Similar to key-value stores, but value is a document (nested values)
  - Examples: MongoDB, CouchDB, etc.

- Wide-Column (Column-Family) stores
  - A column family is a collection of rows and columns,
    where each row has a unique key and each column has a name, value, and timestamp.
  - Examples: BigTable, Hbase, Cassandra, etc.

- Graph databases
  - Nodes and relationships (edges) are the bases of graph databases.
  - Examples: Neo4j, OrientDB, InfoGrid, etc

## CAP theorem

The CAP theorem states that it is impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees:

- Consistency: Every read receives the most recent
  write or an error

- Availability: Every request receives a (non-error)
  response.

- Partition tolerance:
  The system continues operating despite network communication failures between nodes.

### Examples CAP

Fight Booking system use CP

- Consitency: to prevent double booking
- Partition Tolerance: We need information from 2 servers (2 airport) to booking and confirmation

## Index tool

| FAISS Index         | Description                                                        |
| ------------------- | ------------------------------------------------------------------ |
| **IndexIVFFlat** ✅ | Partitions vectors into clusters for faster searching.             |
| **IndexFlatIP**     | Exact similarity search using inner product.                       |
| **IndexHNSW**       | Uses a hierarchical graph for approximate nearest-neighbor search. |
| **IndexLSH**        | Uses locality-sensitive hashing for approximate similarity search. |

## SQL vs NoSQL

| **SQL**                                       | **NoSQL**                                                             |
| --------------------------------------------- | --------------------------------------------------------------------- |
| Relational database                           | Non-relational database                                               |
| Table based                                   | Document based, key-value based, graph data based, wide-column stores |
| predefined schema                             | dynamic schema                                                        |
| Follows ACID properties                       | Follow CAP theorem                                                    |
| Suitable for heavy transactional applications | Not suitable for heavy transactional applications                     |
| No fit for hierachical data                   | Best fit for hierachical data                                         |
| Best for structured data                      | Best for flexible or semi-structured data                             |
| Uses SQL for queries                          | Uses various query languages/APIs                                     |
| Typically scales vertically                   | Typically designed for horizontal scaling                             |
| **Examples:** MySQL, PostgreSQL               | **Examples:** MongoDB, Cassandra, Redis                               |

# Spark and RDD Programming

- Apache Spark is an open-source distributed general-purpose cluster-computing framework.
- Spark aims to be fast: in-memory computing
- Simple differences: Spark vs MapReduce
  - Much faster (in-memory, low latency)
  - Wider range of workloads (e.g. iterative algorithms)

## Language Spark provide

- Java
- Python
- Scala
- R

## Characteristics:

- Speed (in memory)
- Ease of use (more operations than MapReduce, four languages supported)
- A Unified Stack (spark core, SQL, ML, Stream, GraphX)
- Runs Everywhere
  - works with many clusters: Standalone, MESOS, YARN
  - work with many data sources: HDFS, Datawarehouse, NoSQL/SQL database

## RDD

- RDD is a fundamental data structure of Spark.
- RDD is a immutable distributed collection of objects/elements.
- RDD can be self recovered in case of failure (support rebuild if a partition is destroyed).

### RDD Operation

There are two types of RDD Operations: Transformation and Action

#### Transformations

- Transformations are operations on RDDs that return a new RDD.
- Transformed RDDs are computed lazily (only when you use them in an action)
- Many transformations are element-wise (working on one element at a time)

- Examples: map(func), filter(func), flatMap(func), mapValues(func), union(func), reduceByKey(func)

#### Actions

- trigger job execution that forces the evaluation of all the transformations and must return a final value
- the values of action are stored to drivers or to the external storage system.
- It brings laziness of RDD into motion.

- Example: Collect(), count(), reduce(func), take(n), first()

### Lazy

Lazy evaluation means Spark delays executing transformations until an action is called.

#### Main advantage:

- It allows Spark to optimise the execution plan,
- Reducing unnecessary computations
- Reduce number of passes (storage in disk)
- Improving performance.

### RDD Lineage Graph

- Dependencies between RDDs are logged in a lineage graph (or RDD operator graph or RDD dependency graph)
- It is a logical execution plan of RDD transformations

### RDD Persistence and Caching

To reduce computation overhead, RDD persistence is to save the intermediate result.

- Methods:
  - cache(): store all the RDD in-memory (default storage level: MEMORY_ONLY).
  - persist(level): can cache in memory, on disk, or off-heap memory

## Narrow and Wide Dependencies

Narrow transformation (dependencies)

- each partition of the parent RDD is used by at most one partition of the child RDD
- allow for pipelined execution on one cluster node
- failure recovery is more efficient as only lost parent partitions need to be
  recomputed
- Example: map, flatmap, filter, sample, union, etc.

Wide transformation (dependencies)

- multiple child partitions may depend on one parent partition
- require data from all parent partitions to be available and to be shuffled across
  the nodes
- a complete re-computation is needed, if some partition is lost from all the
  ancestors
- Example: groupbyKey() and reducebyKey().

## Shuffle

Shuffle group the records in many nodes with the same key to one partition for further processing.

## Spark workflow

1. **Create** an RDD object;

2. SparkContext is responsible for calculating the
   dependencies between RDDs and **building** DAGs;

3. DAG Scheduler is responsible for decomposing the
   DAG graph into **multiple stages**, each stage
   containing multiple tasks,

4. **Task scheduler** launches tasks to distribute across
   the worker nodes via **cluster manager** (Standalone
   or Mesos or YARN). The task scheduler **does not
   know** about dependencies among stages.

## RDD vs dataFrame

RDD

- is an immutable distributed collection of elements of your data, partitioned across nodes in
  your cluster.
- ls lower-level data abstraction supporting more atomic transformations and action.

DataFrame

- is an immutable distributed collection of data. But it is organized into named columns, like a
  table in a relational database.

- DataFrame is designed to make large data sets processing even easier in some tasks.
- is higher-level data abstraction

Usage cases:

- No-structured data manipulation (RDD) vs large structured data query (DataFrame)

## Examples

Scala

```
val rdd1 = sc.parallelize(array)
val rdd2 = rdd1.map(x => x - 5)
val rdd3 = rdd2.filter(x => x % 2 == 0)
```

```
val lines = sc.textFile("data.txt")
val words = lines.flatMap(line => line.split(" "))
```

# Hadoop MapReduce & HDFS

DFS is a distributed implementation of the time-sharing model of a file system,
where multiple users share files and storage resources.

## Characteristics

- Access transparency
- Location transparency
- Concurrency transparency
- Failure transparency
- Replication transparency
- Migration transparency
- Heterogeneity
- Scalability

## NFS

- Network File System (NFS) is a distributed file system protocol
- NFS is a client-server application, where a user can view, store and update the files on a remote
  computer.
- Advantages:
  - easy sharing of data across clients
  - centralized administration
  - security (put server behind firewall)

## CFS

- Clustered File System (CFS) is not a single server but instead a cluster of servers
  that all work together to provide high performance service to their clients.

## GFS

- Google File System is a scalable distributed file system developed by Google to provide efficient,
  reliable access to data using large clusters of commodity hardware.

Workloads : two kinds of reads and writes - Large streaming reads (1MB or more) and small random reads (a few KBs) - Sequential appends to files by hundreds of data producers
High sustained throughput is more important than latency

GFS (Google File System) supports:

- Read: Retrieve data from files.
- Write: Write data to files.
- Create: Create new files.
- Delete: Remove files.
- Append: Add data to the end of a file.
- Snapshot: Create a copy of a file or directory.

### GFS overviews

Files stored as chunks

- With a fixed size of 64MB each.
- With a 64-bit ID each.

Reliability through replication

- Each chunk is replicated across 3 (by default) or more
  chunk servers
- Replication number can be manually set

Single Master

- Centralized management
- Only store meta-data

### READ

1. Client Request: The application requests a file through the GFS client which sends the file name and chunk index to the Master.

2. Master Response: The Master returns the chunk handle and locations (IP addresses) of all chunk replicas.

3. Client Cache: The client caches this information and contacts the closest Chunk Server, specifying the chunk handle and byte range.

4. Read Data: The Chunk Server sends the requested data directly to the client, without further Master interaction while the cached information remains valid.

5. Return Data: The client forwards the data to the application.

### WRITE

1. Client Request: The client asks the Master for the primary Chunk Server (lease holder) and locations of secondary replicas.

2. Master Response: The Master returns the primary and secondary replica locations.

3. Push Data: The client sends data to all replicas and waits for acknowledgements.

4. Write Request: The client sends a write request to the primary, which assigns serial numbers to ensure mutations are applied in order.

5. Replicate Write: The primary forwards the write request to secondary replicas, which apply mutations in the same order.

6. Acknowledgement: Secondary replicas confirm completion to the primary, which then returns a success or error message to the client.

## HDFS

HDFS (ID60, Lec10, 37-50)

- Similar motivations:
- Many inexpensive commodity hardware and failures are very common
- Many big files: millions of files, ranging from MBs to GBs
- Two types of reads
  - Large streaming reads
  - Small random reads
- Once written, files are seldom modified
- Random writes are supported but do not have to be efficient
- High sustained bandwidth is more important than low latency
- Block size is 128MB (by default)

# Model as a service

- hosting pre-trained ML models on cloud infrastructure and
  making them accessible via APIs. This setup allows organisations to take advantage
  of ML models without having to create and train them from scratch.

## Pros

- Make much easier for businesses of all sizes to build, deploy, and maintain AI solutions, and integrate AI into their applications.

## Simple chatbot workflow:

1. **Receive User Input:** The backend authenticates the user and receives their text or request.
2. **Construct Context:** Combine the task instructions, user input, and relevant conversation history.
3. **Call Hosted Model:** Send the input to the model API, which generates a response using its existing weights.
4. **Return Generated Text:** Check the API response and display the result to the user without sending the email.

## Simple RAG

### RAG Assistant Workflow

1. **Receive Question:** Identify the user's question and check which documents they are authorised to access.
2. **Retrieve Passages:** Search relevant documents using embeddings and a vector database.
3. **Add Context:** Combine the question, retrieved passages, and source references, then send them to the hosted model.
4. **Return Answer:** Provide an answer supported by sources. If evidence is insufficient, state the limitation instead of inventing information.

### Tool-Using Agent Workflow

1. **Interpret Task:** Understand the user's request, available tools, and collect any missing information.
2. **Validate Tool Call:** The model proposes a tool and arguments. Checks permissions, input format, and required approvals.
3. **Execute Tool:** Call the authorised API or database and collect the actual result or error.
4. **Continue or Finish:** Return the result to the model, which either performs another validated step or reports the outcome within time, cost, and call limits.

# Security & Privacy

- Asymmetric encryption relies on the use of two different keys, namely a private key and a public
  key.
- The private key is known only to its owner
- the public key is commonly available.
- A document that was encrypted with a public key can only be correctly decrypted with the
  corresponding private key.
- asymmetric encryption is almost always computationally slower than symmetric encryption.
- Typical algorithms: RSA etc

## Hashing

- The hashing mechanism is used when a one-way, non-reversible form
  of data protection is required.
- Once hashing has been applied to a message, it is locked and no key is
  provided for the message to be unlocked.
- Hashing technology can be used to derive a hashing code or message
  digest from a message, which is often of a fixed length.

## Digital Signatures

The digital signature mechanism is a means of providing data authenticity and integrity through
authentication and non-repudiation.

- A message is assigned a digital signature prior to transmission,
- The signature will become invalid if the message has unauthorized modifications.
- A digital signature provides evidence that the message received is the same as the one created by
  its rightful sender.

### Process

Process:

1. The sender selects the file to be digitally signed in the document platform or application and calculates
   the unique hash value of the file content (1-hashing).

2. This hashed value is encrypted with the sender’s private key (2- encrypt with private key) to create the
   digital signature
3. The digital signature is appended to the plain text message (3-append).

4. The receiver use the same hash function to calculates the hash value of the plain text messages (4-
   hashing)

5. The receiver decrypt the digital signature with sender’s public key (5- decrypt with public key).

6. The receiver compares the hash value of the plain text in Step 4 and the decrypted digital signature in
   Step 5 (6-Compare)
