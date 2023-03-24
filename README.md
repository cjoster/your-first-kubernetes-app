
# Your First Kubernetes Application

This guide is intended to walk a new user through starting from
scratch and deploying a working, web-accessible, "Hello World"-type
application in Kubernetes. It is not intended to cover every topic
imaginable, but to serve as a quick-start resource to get up and running
on a kubernets cluster quickly.

If you would like to contribute to this tutorial or fix an error of some
kind, pull requests are welcome.

# Table of Contents

1. [Working with Git](01-Working-With-Git)
    1. [Installing Git](01-Working-With-Git#installing-git)
        1. [DNF Based Linux Distributions](01-Working-With-Git#installing-dnf)
        2. [Yum Based Linux Distributions](01-Working-With-Git#installing-yum)
        3. [Debian Based Linux Distributions](01-Working-With-Git#installing-deb)
        4. [MacOS](01-Working-With-Git#installing-macos)
        5. [Windows](01-Working-With-Git#installing-windows)
    2. [Cloning This Git Repository](01-Working-With-Git#cloning-git) 
2. [Building Your First Container](02-Building-Your-First-Container)
    1. [Containerfiles](#containerfiles)
    2. [Containerfile explanation](#containerfile-explanation)
    3. [Building the Container](#building-the-container-image)
        1. [Building the Container With `podman`](#podman)
        2. [Building the Container With `buildah`](#buildah)
        3. [Building the Container With `docker`](#docker)
