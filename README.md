## Elasticsearch training lab
This is a simple lab environment for training and experimenting with Elasticsearch 7.4.0.

It will build nodes running on CentOS, and provision them with the required system settings to run Elasticsearch on a non-local IP. It's a naive method of provisioning but it's suitable for our requirements.

The lab is designed purely as a training tool. It doesn't use all the best practices for a production cluster and shouldn't be considered suitable for one.

If you are studying for Elastic Certified Engineer, or you've been on the Elasticsearch Engineer I and/or II courses, this lab will help you get familiar with the environment used in the exam and run the labs from the courses. The main difference is that we're using Vagrant here so need to run `vagrant ssh` instead of just `ssh`. If you would rather use SSH directly, you'll need to do some work to copy your public keys into the VMs.

### Dependencies
These two archives are required:
- [Elasticsearch 7.4.0](https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.4.0-linux-x86_64.tar.gz)
- [Kibana 7.4.0](https://artifacts.elastic.co/downloads/kibana/kibana-7.4.0-linux-x86_64.tar.gz)

### Running
- Install VirtualBox
- Install Vagrant
- Clone this repository
- Place the Elasticsearch and Kibana archives into the repository root
- `cd` into the repo
- Run `vagrant up`

Without modifying `Vagrantfile`, Vagrant will spin up two VMs; one Elasticsearch node (`10.0.200.101`) and one instance of Kibana (`10.0.200.104`).

To start Elasticsearch, you can `vagrant ssh node1` and run `elasticsearch-7.4.0/bin/elasticsearch`. 

To start Kibana, you'll need to `vagrant ssh node4` and run `kibana-7.4.0/bin/kibana`. 

If you need more nodes, you can uncomment the provisioners for `node2` and `node3`, then run `vagrant up` again. When you start Elasticsearch on those nodes, they'll automatically join the cluster and shard reallocation will begin.

### Resetting
If you've been using the environment and want/need to burn everything down and start from scratch, you can use `vagrant destroy`. This will delete the VMs so the next time you `vagrant up`, you'll get a brand new cluster.
