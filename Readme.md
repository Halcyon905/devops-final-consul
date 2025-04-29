# Demo project accompanying a [Consul crash course video](https://www.youtube.com/watch?v=s3I1kKKfjtQ) on YouTube

This demo project is sourced from this git [repository](https://gitlab.com/twn-youtube/consul-crash-course) hosted on Gitlab. The repository is made by the Youtube channel [TechWorld with Nana](https://www.youtube.com/@TechWorldwithNana).

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

# GCP source codes

This demo project is sourced from this git [repository](https://github.com/GoogleCloudPlatform/microservices-demo) made by Google Cloud Platform. It is a sample cloud-first application with 10 microservices showcasing Kubernetes, Istio, and gRPC.

**Online Boutique** is a cloud-first microservices demo application.  The application is a
web-based e-commerce app where users can browse items, add them to the cart, and purchase them.

Google uses this application to demonstrate how developers can modernize enterprise applications using Google Cloud products, including: [Google Kubernetes Engine (GKE)](https://cloud.google.com/kubernetes-engine), [Cloud Service Mesh (CSM)](https://cloud.google.com/service-mesh), [gRPC](https://grpc.io/), [Cloud Operations](https://cloud.google.com/products/operations), [Spanner](https://cloud.google.com/spanner), [Memorystore](https://cloud.google.com/memorystore), [AlloyDB](https://cloud.google.com/alloydb), and [Gemini](https://ai.google.dev/). This application works on any Kubernetes cluster.

| Service                                              | Language      | Description                                                                                                                       |
| ---------------------------------------------------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [frontend](/src/frontend)                           | Go            | Exposes an HTTP server to serve the website. Does not require signup/login and generates session IDs for all users automatically. |
| [cartservice](/src/cartservice)                     | C#            | Stores the items in the user's shopping cart in Redis and retrieves it.                                                           |
| [productcatalogservice](/src/productcatalogservice) | Go            | Provides the list of products from a JSON file and ability to search products and get individual products.                        |
| [currencyservice](/src/currencyservice)             | Node.js       | Converts one money amount to another currency. Uses real values fetched from European Central Bank. It's the highest QPS service. |
| [paymentservice](/src/paymentservice)               | Node.js       | Charges the given credit card info (mock) with the given amount and returns a transaction ID.                                     |
| [shippingservice](/src/shippingservice)             | Go            | Gives shipping cost estimates based on the shopping cart. Ships items to the given address (mock)                                 |
| [emailservice](/src/emailservice)                   | Python        | Sends users an order confirmation email (mock).                                                                                   |
| [checkoutservice](/src/checkoutservice)             | Go            | Retrieves user cart, prepares order and orchestrates the payment, shipping and the email notification.                            |
| [recommendationservice](/src/recommendationservice) | Python        | Recommends other products based on what's given in the cart.                                                                      |
| [adservice](/src/adservice)                         | Java          | Provides text ads based on given context words.                                                                                   |
| [loadgenerator](/src/loadgenerator)                 | Python/Locust | Continuously sends requests imitating realistic user shopping flows to the frontend.                                              |
