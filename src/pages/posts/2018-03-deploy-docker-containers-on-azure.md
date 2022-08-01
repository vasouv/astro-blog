---
layout: "../../layouts/BlogPost.astro"
title: "Deploy Docker containers on Azure"
description: "Example on how to deploy Docker containers on Microsoft Azure"
publishDate: "20 Mar 2018"
categories: 
  - "azure"
---

Recently I had to use Azure to deploy Docker containers and was amazed by how simple the platform is, at least to deploy a container without any other configuration. I didn't use any load balancers, service registries, etc... My experiments are very simple because currently I don't need much cloud functionality.

Since it was so easy to upload and run Docker containers on Azure, I decided to write a blog post so here it goes.

# Use case:

I want to upload two Docker containers and make them communicate with each other. One will be the "backend" and the other the "frontend". Both use JAX-RS to expose a String. We only access the "frontend" which takes a String from the "backend" and returns two greetings.

# Create Azure Container Registry:

From the Azure dashboard, we go to **Create a resource** > **Containers** > **Azure Container Registry**.

The **Registry Name** is self-explanatory, let's say "vasouvAzureTest". For the **Resource Group**, we can either add the registry in an existing resource group or create a new one. I'm creating a new one so I give it a name "vasouvAzureTestRG". For the **Location** obviously choose what is closer to you, I have "West Europe". **SKU**s are the capabilities of the registries, how much storage they have, how they scale etc... I want the registry for testing purposes so I go with the "Basic".

Click "Create" and wait until the deployment is complete.

## Get admin credentials

To upload a Docker image to the repository, we need the admin credentials to login from the command line.

We navigate to the registry, then **Access Keys** and **Enable Admin**. We need the **login server**, **username** and **password** so take a note of them.

![registry access keys](/assets/2018-03-docker-containers-on-azure/registry-access-keys.png)

Now we're ready to upload the Docker images to the registry.

# Login to Azure Container Registry:

We'll use Docker from the command line to connect to ACR and push our images. The login stays for hours so we don't have to connect frequently. If the login is successful it should say "Login Succeeded".

![carbon](/assets/2018-03-docker-containers-on-azure/carbon.png)

# Build and push an image to ACR:

First we'll build and upload the "backend" container to see that it really works.

![carbon (1)](/assets/2018-03-docker-containers-on-azure/carbon-1.png)

The first command builds the image according to the name we give it, it can be anything but a common habit is to use the repository name and the image name after the slash.

Then we tag the image to conform to how Azure wants it, basically the login server and then the image name.

Last command pushes the image to our repository.

Now if we go to our container registry, we should see the repository created for our image.

# Run a container:

It's so easy to run a container on Azure, see the screenshot.

![run container](/assets/2018-03-docker-containers-on-azure/run-container.png)

Of course we must configure the container! I want to name it "azure-kumuluzee-backend" and use the existing resource group we created earlier. **Number of cores** and **Memory** we leave at default and select port 8080.

For the sake of the test and to see if the container works correctly, I want to have a **Public IP**. If it was a service we didn't want to expose to the world, we'd click "No".

Click OK and wait till the instance is deployed.

# Access the service:

To see our deployed container we can go to the resource group.

![find container](/assets/2018-03-docker-containers-on-azure/find-container.png)

If we click on it, we see its properties. For now, we're interested in the IP address field.

Browse to it at the 8080 port, find your REST resource and you should see the response.

# Build, upload and run the "frontend" service:

Since we 're using the JAX-RS Client API to retrieve the data from the "backend" service, we probably have something like

`http://localhost:8080/kumuluzee-backend/greeting`

as the client's target. Now that we're targeting an online resource, it must change and instead of localhost put the public IP of the backend container.

If all goes well, we should see both responses from the frontend container:

```
Hello from the KumuluzEE backend service 1521540108783
Hello from the frontend 1521540108787
```

The resource group with the two running containers, and the repositories should like below:

\[gallery ids="649,650" type="rectangular"\]

# Conclusion

That's it! The Azure platform makes it ridiculously easy to upload Docker containers and run them without effort. All we have to do is point to the correct IP address the other containers run on.

This experiment was with just two containers. It's another story to deploy a swarm with load balancing, orchestration etc.
