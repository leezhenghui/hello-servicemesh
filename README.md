## Introduction

The purpose of this repository aims to provide a hands-on architecture PoC(proof-of-concept) sample that demonstrate how to **build** and **run** a `microservices architecture`(MSA) application(multiple programming languages) with the capabilities of service registry, naming resolution, client service disovery, client load balance, traffic shapping, failure tolerance, etc. 

## PoC Scenario 

The sample contains Java and Node.js modules. In reality, the RPC framework usually are programming language specific, so the challenge for us is how to enable a MSA application with mixed-languages. This sample will show you the approach of service fabric(servicemesh) pattern.

### Overview

![PoC Scenario Overview](./docs/architecture-servicemesh-components.png)

### Run the Sample 

For each service, we will schedule two instances and check the service discovery and load balance result.

#### Steps

- Git clone the project

	On host:
  ```shell
  git clone git@github.com:leezhenghui/hello-servicemesh.git
  ```

- Gradle build/deploy distribution
  
	On host:
	```shell
	cd hello-servicemesh
  gradle deploy 
  ```

- Launch VM 
  
	On host:
	```shell
	cd ops
	vagrant up
  ```

- Provision the VM 
  
	On host:
	```shell
	vagrant provision 
  ```

- Start all nomad jobs 

  For each services, two intances will be created for a load balance, service discovery testing
  
	On host:

	```shell
  vagrant ssh
  ```

	In VM
	```shell
	cd /vagrant/bin
	./start_all_jobs.sh
	```

- Run the sample 

  In VM:
	```shell
	./click.sh
  ```

- Run benchmark 

  In VM:
	```shell
	./benchmark.sh
  ```

#### Result of Service Discovery and Load Balance

![loadbalance-result](./docs/loadbalance-result.png)
