# kafka-machine
Vagrant dev machine provisioned using Ansible

## Software versions

- Vagrant 1.9.5
- Oracle Virtual Box 5.1.22 (running on Windows 7)


## Kafka and zookeeper

This will install kafka and zookeeper.  You can set up the number of brokers you want by editing the "kafka_brokers" dictionary variable.  Currently only 1 zookeeper instance is set up.
