# Deploying Your Container Image

In this step, you'll learn how to tag and push an container image
into a container registry. If you already have a registry--you'll need one
to deploy your container--you can skip most of the steps regarding DockerHub.

1. [Create a DockerHub Account](#create-a-dockerhub-account)

4. [Next Steps](#next-steps)

# Create a DockerHub Account

Head over to DockerHub at [https://hub.docker.com](https://hub.docker.com) and create an account.

Once you create an account, you'll need to confirm your email address by clicking on the link sent to your email
address.

# Create the Repository

Once signed into DockerHub and with your email verified, hit the **Create Repository** button. You'll select
your username in the "Namespace" drop-down, and enter "phpdemo" into "Repository Name" field. You can leave the
description empty or fill it out if you feel like it.

# Tag your image

Back on your terminal, you'll need to tag the container image with the repository. Tags are simply labels
that tell you where the image came from. They are in the form of `<registry host>/<library path>/<container name>:<version>`.

So, to tag your image for publishing to docker hub, you'll run the following command. Replace `<your username>` with your DockerHub username.

```bash
podman tag localhost/phpdemo:0.1a docker.io/<your username>/phpdemo:0.1a
```

# Login to DockerHub

Next, we need to login to DockerHub from the command-line in order to push our image. Run the following command:

```bash
podman login docker.io
```

Enter your username and password that you used to create your account.

# Push your image

Once logged in, you issue the push command:

```bash
podman push docker.io/<your username>/phpdemo:0.1a
```

# Delete the image and pull

**OPTIONAL**

If you want to verify the push, you can go to another machine and pull, or you can delete the local copy of the image.
You'll have to delete both tags in order to fully delete the image.

```bash
podman rmi docker.io/<your username>/phpdemo:0.1a
podman rmi localhost/phpdemo:0.1a
```

Next, attempt to pull the image:

```bash
podman pull docker.io/<your username>phpdemo:0.1a
```

And you'll see output something similar to:

```
Trying to pull docker.io/cjoster/phpdemo:0.1a...
Getting image source signatures
Copying blob fac8e70fcf67 done  
Copying blob ee0a4e40ccac done  
Copying blob f1f26f570256 [================================>-----] 25.9MiB / 30.0MiB
Copying blob 5baa808a48ff done  
Copying blob 6e8d74e4d8ee done  
Copying blob 5ca9fb408faa [===========>--------------------------] 26.8MiB / 87.4MiB
Copying blob b3b7906fb177 done  
Copying blob cb4935bbeb83 done  
Copying blob c9e00ef337e3 done  
Copying blob cfe495c8d695 done  
Copying blob dcc3fd107f0c done  
Copying blob fe3c587d1f07 done  
Copying blob 677f27d94442 done  
Copying blob f87a2e4bd29c done  
Copying blob 9f00f26c50b0 done  
```

# Next steps

Once you have deployed your image, you can head over to the next step: [Publishing Your Container Image](../04-Publishing-Your-Container-Image)
or head back to the [Table of Contents](../../../) and navigate from there.

