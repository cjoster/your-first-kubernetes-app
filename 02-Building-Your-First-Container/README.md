# Building Your First Container Image

Building container images is a central theme to kubernetes and
a process you will need to understand in depth. Of course, application teams
will build their applications into containers, but platform
administrators need to not only understand the process to support
the application teams, there are many good reasons to build platform-related
containers. From troubleshooting containers, to packaging in-house platform-related
tools, platform administrators will find themselves building containers regularly.

Steps to build containers are here

1. [Containerfiles](#containerfiles)
2. [Containerfile explanation](#containerfile-explanation)
3. [Building the Container](#building-the-container-image)
    1. [Building the Container With `podman`](#podman)
    2. [Building the Container With `buildah`](#buildah)
    3. [Building the Container With `docker`](#docker)
4. [Next Steps](#next-steps)

## Containerfiles

Container images, (previously called "Docker images") are defined by a file
called a Containerfile. Their syntax is pretty straightforward, but can also get
as complicated as you need it to be.

Containerfiles used to be called Dockerfiles. Some tools can work with either naming
mechanism. Others will require the file be named one of those two things. These days,
we refer to them as Containerfiles owing to the now open standard that was started
as Dockerfile.

This tutorial is not intended to be a complete reference for everything that you can do in a
Containerfile. More information can be found in the man pages on your system (`man Containerfile`),
over at the [Dockerfile specification](https://docs.docker.com/engine/reference/builder/).

The Containerfile for this tutorial is [in the `Containerfile` file](Containerfile) in this
directory. It is also included here for explanation:

```Containerfile
FROM php:8.1.17-apache

# Copy apache configuration
COPY apache2 /etc/apache2

# Copy our site
COPY src /var/www/html
```

## Containerfile Explanation

The `FROM` line tells the underlying engine to download the `php`
base container, specifically the `8.1.17-apache` version. This is
so that we can run php scripts inside the Apache web server.

The next `COPY` line copies some overriding of the Apache configuration
in that container that we had to do in order to get the container to
run correctly in a secure environment (more on that later).

The last `COPY` directive copies our hello-world application into
the resulting container image. The application is mostly HTML with
a single executed line of PHP:

```php
<HTML>
	<HEAD>
		<TITLE>
			Hello World!
		</TITLE>
	</HEAD>
	<BODY>
		<?php
			print "Hello world from php-apache.\n"
		?>
	</BODY>
</HTML>
```

## Building the container image

Building the container file is pretty straight forward. These
days, there are several options for building them. 
The typical options are
`podman`, `buildah`, or `docker`. Installing Docker Desktop is outside
of the scope of this tutorial. Installing `buildah` or `podman` is done the
same way you installed `git`.

The least-privilege way to build a container at the time of this writing
is `podman`.

### Podman

You can build the container image using `podman` by running the following
command:

```bash
podman build -t phpdemo:0.1a .
```

Which should give you an output similar to this:

```
STEP 1/3: FROM php:8.1.17-apache
STEP 2/3: COPY apache2 /etc/apache2
--> f67faacbcfe
STEP 3/3: COPY src /var/www/html
COMMIT phpdemo:0.1a
--> ea4ef653767
Successfully tagged docker.io/cjoster/phpdemo:0.1a
ea4ef65376706072e51d19987a7ddae6291bf55373d86abde32b1c6a5c492e3e
```

You can view the resulting image by running...

```bash
podman images
```

Which will look something like the following:

```
REPOSITORY                         TAG            IMAGE ID      CREATED         SIZE
localhost/phpdemo                  0.1a           68f13e79912f  11 seconds ago  468 MB
docker.io/library/php              8.1.17-apache  164432f6f3a7  32 hours ago    468 MB
```

### Buildah

Buildah is another option to build containers. Invoke it with the following command:

```bash
buildah build -t phpdemo:0.1a .
```

Which will give you outputs similar to the following:


```
STEP 1/3: FROM php:8.1.17-apache
STEP 2/3: COPY apache2 /etc/apache2
STEP 3/3: COPY src /var/www/html
COMMIT phpdemo:0.1a
Getting image source signatures
Copying blob 3af14c9a24c9 skipped: already exists  
Copying blob b45c80a24442 skipped: already exists  
Copying blob c4bd73e3313b skipped: already exists  
Copying blob d49b6de95451 skipped: already exists  
Copying blob c7d8897e4c71 skipped: already exists  
Copying blob a9a38a747fd3 skipped: already exists  
Copying blob 99af6c8cd2cd skipped: already exists  
Copying blob 828367486dfb skipped: already exists  
Copying blob 2534f48fcd7b skipped: already exists  
Copying blob 27a1f496f09b skipped: already exists  
Copying blob d0debd5845de skipped: already exists  
Copying blob 8e292d6d94e9 skipped: already exists  
Copying blob 28d4ed881e97 skipped: already exists  
Copying blob 3d95406448cd done  
Copying config 5cf7c94312 done  
Writing manifest to image destination
Storing signatures
--> 5cf7c943126
Successfully tagged localhost/phpdemo:0.1a
```

...and view the resultant image:

```bash
buildah images
```

Which will look something like:

```
REPOSITORY                          TAG             IMAGE ID       CREATED              SIZE
localhost/phpdemo                   0.1a            5cf7c943126d   About a minute ago   468 MB
docker.io/library/php               8.1.17-apache   164432f6f3a7   32 hours ago         468 MB
```

### Docker

If you have docker desktop and wish to use it to build your container,
you can. But first, you have to 

```
ln -s Containerfile Dockerfile
```

**or**

```bash
mv Containerfile Dockerfile
```

**then:**

```bash
docker build -t phpdemo:0.1a .
```

followed by...

```bash
docker images
```

# Next steps

Once you have built the image, you can head other to the next step: [Testing Your Container Locally](../03-Testing-Your-Container-Locally)
or head back to the [Table of Contents](../../../) and navigate from there.

