# Testing Your Container Locally

In this step, you'll learn how to launch your container locally
on the machine on which it was built. This can be done with `podman`
or `docker`. 

1. [Launching Your Container With Podman](#launching-your-container-with-podman)
2. [Testing Your Container](#testing-your-container)
3. [Docker](#docker)
4. [Next Steps](#next-steps)

## Launching Your Container With Podman

Once you have an image, which you can view with the `podman images` command, launching the image
is done with the following command:

```bash
podman run -p 8080:8080 localhost/phpdemo:0.1a
```

...and the pod should start up. The arguments `-p 8080:8080` are in the form of `-p <local port>:<container port>`.
Apache in the container is configured to listen on port 8080. If 8080 is in use on your local machine, you can specify
`-p 8081:8080` (or any other port for that matter).

You can also tell `podman` to detach the container from the terminal by passing a `-d` argument. Additionally, you can tell `podman`
`podman` to remove the container when it exists with the `--rm` flag. The full command would look like:

```bash
podman -d --rm -p 8080:8080 localhost/phpdemo:0.1a
```

## Testing your container

Once the container us running, you can test it's output using `curl`:

```bash
curl http://localhost:8080
```

You can also visit that URL in a browser if you have the ability to launch a browser (i.e. you're not building
your image on a remote, headless jump box).

## Docker

The command syntax for docker is identical to the `podman` syntax.

# Next steps

Once you have tested your image locally, you can head other to the next step: [Publishing Your Container Image](../04-Publishing-Your-Container-Image)
or head back to the [Table of Contents](../../../) and navigate from there.

