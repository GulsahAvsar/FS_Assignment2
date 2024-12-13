# Best Buy Cloud-Native Application
## Application Architecture

![app_architecture](https://github.com/user-attachments/assets/a2ff1c31-d9a7-40ff-87ea-8ef851f4c812)


## Application and Architecture Explanation

### Architecture

This application is a cloud-native system for Best Buy that supports customer and employee interactions, order processing, inventory management, and AI-driven services.
Key users are customers and employees as shown in the diagram.

**store-front-best-buy** acts as the front-end for customers, allowing them to browse products, place orders, and interact with the system.

**store-admin-best-buy** enables employees to manage operations, such as inventory, product updates, and order fulfillment.

**order-service-best-buy** handles order placements by customers. Processes these orders and sends them to the Azure Service Bus, which queues them for further processing.

**product-service-best-buy** manages product information, such as inventory and availability. Interacts with MongoDB for data storage.

**makeline-service-best-buy** processes orders from employees and customers, ensuring order fulfillment and updates in the order database.

**ai-service-best-buy** uses AI capabilities to enhance customer and employee interactions. For example, the GPT-4 model powers intelligent responses, and the DALL-E model generates custom images.

### Information Flow

Customers interact with store-front-best-buy to browse and place orders.
Orders are processed by order-service-best-buy, which utilizes the Azure Service Bus for queuing.
Employees use store-admin-best-buy to manage operations like product updates and processing orders.
Product data is fetched and updated by product-service-best-buy with data stored in MongoDB.

## Deployment Instructions

### Step 1: best-buy-all-in-one.yaml

After updating all services, I pushed them to github separately. Then I build docker images and pushed them to docker desktop. I updated the best-buy-all-in-one.yaml with new docker images. 
This file takes place under Deployment files folder and includes all necessary Kubernetes resources.

### Step 2: Set up AKS Cluster

I created an AKS clusters with one worker node. 

Log in to Azure Portal.

Create a Resource Group called FullStackLAB2 in Canada region.

**Create an AKS Cluster**

In the Azure Portal, under Kubernetes services create and select Kubernetes cluster.
In the Basics tap fill in the following details:
*Subscription: Select your subscription.
*Resource group: Choose FullStackLAB2
*Cluster preset configuration: Choose Dev/Test.
*Kubernetes cluster name: BestBuyCluster
*Region: Same as your resource group (e.g., Canada).
*Availability zones: None.
*AKS pricing tier: Free.
*Kubernetes version: Default.
*Automatic upgrade: Disabled.
*Automatic upgrade scheduler: No schedule.
*Node security channel type: None.
*Security channel scheduler: No schedule.
*Authentication and Authorization: Local accounts with Kubernetes RBAC.
*In the Node pools tap fill in the following details:
*Select agentpool. Optionally change its name to masterpool. This nodes will have the controlplane.
*Set node size to D2as_v4.
*Scale method: Manual
*Node count: 1
*Click update
*Click on Add node pool:
*Node pool name: workerspool.
*Mode: User
*Set node size to D2as_v4.
*Scale method: Manual
*Node count: 1
*Click add
*Click Review + Create, and then Create. The deployment will take a few minutes.

### Step 3: Connect to AKS Cluster via Visual Studio

Once the AKS cluster is deployed, navigate to the cluster in the Azure Portal.

In the overview page, click on Connect.

Select Azure CLI tap.

Login to your azure account using the following command:

```bash
az login
```

Set the cluster subscription using the command shown in the portal 

```bash
az account set --subscription 'subscription-id'
```

Copy the command shown in the portal for configuring kubectl





![store-front1](image.png)

![store-front-products](image-4.png)

![store-admin-orders](image-2.png)

![complete order](image-3.png)

## Table of Microservice Repositories

| Service               | Repository Link     |
|-----------------------|---------------------|
| Store-Front           | [store-front-best-buy](https://github.com/GulsahAvsar/store-front-best-buy.git)   |
| Order-Service         | [order-service-best-buy](https://github.com/GulsahAvsar/order-service-best-buy.git)   |
| Product-Service       | [product-service-best-buy](https://github.com/GulsahAvsar/product-service-best-buy.git)   |
| Store-Admin           | [store-admin-best-buy](https://github.com/GulsahAvsar/store-admin-best-buy.git)   |
| Makeline-Service      | [makeline-service-best-buy](https://github.com/GulsahAvsar/makeline-service-best-buy.git)   |
| AI-Service            | [ai-service-best-buy](https://github.com/GulsahAvsar/ai-service-best-buy.git)   |



## Table of Docker Images

| Service               | Docker Image Link                           |
|-----------------------|---------------------------------------------|
| Store-Front           | [gulsahavsar/store-front-best-buy](https://hub.docker.com/repository/docker/gulsahavsar/store-front-best-buy/general)                     |
| Order-Service         | [gulsahavsar/order-service-best-buy](https://hub.docker.com/repository/docker/gulsahavsar/order-service-best-buy/general)                     |
| Product-Service       | [gulsahavsar/product-service-best-buy](https://hub.docker.com/repository/docker/gulsahavsar/product-service-best-buy/general)                     |
| Store-Admin           | [gulsahavsar/store-admin-best-buy](https://hub.docker.com/repository/docker/gulsahavsar/store-admin-best-buy/general)                     |
| Makeline-Service      | [gulsahavsar/makeline-service-best-buy](https://hub.docker.com/repository/docker/gulsahavsar/makeline-service-best-buy/general)                     |
| AI-Service            | [gulsahavsar/ai-service-best-buy](https://hub.docker.com/repository/docker/gulsahavsar/ai-service-best-buy/general)                     |





## Any issues or limitations in the implementation


## Demo Video


