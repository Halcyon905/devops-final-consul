# Demo project accompanying a [Consul crash course video](https://www.youtube.com/watch?v=s3I1kKKfjtQ) on YouTube

## Terraform

1. `providers.tf` - tells terraform which cloud provider we are using.
2. `variables.tf` - some variables to be used in creating resources in the cloud platform.
3. `main.tf` - contains definitions and attributes used to create resources.

## Kubernetes

1. `config-consul.yaml` - config file which creates deployments and services for the online store web page in the cloud. It is the same as the second file, but used after deploying `Consul` to the cluster. It adds annotations in order to attach metadata to objects so that the objects can connect to the required services.
2. `config.yaml` - config file used before deploying `Consul` which creates deployments and services for the online store web page in the cloud.
3. `consul-mesh-gateway.yaml` - creates a mesh gateway used to connect 2 cloud platforms together.
4. `consul-values.yaml` - configuration values for installing Consul using helm.
5. `exported-service.yaml` - used to export the shippingservice from the second cloud platform (Linode) to the first cluster on EKS.
6. `service-resolver.yaml` - used to set the imported `shippingservice` from the second cluster on Linode as a failover for the first cluster on EKS.