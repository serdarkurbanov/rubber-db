# rubber-db
cloud-native scalable elastic NoSQL database

# goal
make infinitely scalable and elastic (runtime-scalable) database that would deploy with same scaling factor as microservices

# idea
## general idea
Partition database in microdeployments, each having as little data as required to easily copy this data to another small instance in runtime under reasonable SLA (1 min for instance)

# necessary gossip mechanism
Swarm of rubber-db nodes will need to self-organize and self-configure at any scale. All parts of configuration that depend on number of instances (partitioning etc) need to be based on consensus mechanism such as Raft leader elections. Configuration that is not dependent on scale (number of replications etc) can be provided in configuration file.

# separate read-write scaling
Write replicas and read replicas are deployed as separate instances and are scaled separately

# managers and workers
rubber-db needs separating nodes into managers and workers, managers being responsible for runtime self-configuration and redistribution of data with scaling
