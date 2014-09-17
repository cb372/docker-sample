An example Dockerfile for a Java webapp + a few dependencies:

 * JDK 8
 * Nginx
 * git 1.7
 * Maven 3.1.1

Prerequisites
-----

I assume you have installed Docker and it is running.

See the [Docker website](http://www.docker.io/gettingstarted/#h_installation) for installation instructions.

Build
-----

Steps to build a Docker image:

1. Clone this repo

        git clone https://github.com/cb372/docker-sample.git

2. Manually download JDK 8u20 (x64 rpm) from the Oracle site

3. Copy the JDK rpm to the appropriate folder

        cd docker-sample
        mkdir jdk
        cp ~/Downloads/jdk-8u20-linux-x64.rpm jdk

4. Build the image

        cd ..
        docker build -t="my-app" docker-sample

    This will take a few minutes.

5. Run the image's default command, which should start everything up. The `-p` option forwards the container's port 80 to port 8000 on the host. (Note that the host will actually be a guest if you are using boot2docker, so you may need to re-forward the port in VirtualBox.)

        docker run -p="8000:80" my-app

6. Once everything has started up, you should be able to access the webapp via [http://localhost:8000/](http://localhost:8000/) on your host machine.

        open http://localhost:8000/

You can also login to the image and have a look around:

    docker run -i -t my-app /bin/bash
