# Docker Commands

## Routes
- [About](About)
- [Quick start](Quick-start)
- [Docker image](Docker-image)
- [Docker container](Docker-container)
- [Docker volumes](Docker-volumes)

## About
The main commands wich always use.
> Recommended know `bash` commands, also `go` language

## Quick start
Here is instruction, how run your project on docker.

### Install Docker 
First you must install docker. 

#### if you use 
- `WSL 2` read [this](https://docs.microsoft.com/ru-ru/windows/wsl/tutorials/wsl-containers)
- `Windows` or `Linux` read [this](https://hub.docker.com/)

### Create Image
And you must create `Dockerfile`.

#### Explaining:
Lets watch what we have in `Dockerfile` with using comamnd `cat` on bash
```bash
$ cat Dockerfile
# if you use golang application, you should write golang instead {IMAGE}
# Example "FROM golang"
FROM {IMAGE}
# Your application be here. (Not important, but this is GOOD PRACTICE)
# Example "WORKDIR /app"
WORKDIR {/folder}
# It means COPY FROM TO
## FROM - On your local storage
## FROM == . - Where Dockerfile
## TO - On inner docker container
## TO == . - Your WORKDIR. Also you can write /app
## . - means this directory or workdirectory
COPY . . 
# RUN - Runs 1 time when BUILDING container. I mean if you restart your container again it will not execute.
## Example "RUN go build -o program main.go"
RUN {COMMANDS}
# CMD - Commands wich EXECUTING on runs your container. I mean every time when you restart container. 1 argument 1 value on CMD.
## Example 'CMD ["./program"]' or 'CMD ["go", "run", "main.go"]'
CMD ["{EXECUTE}"]
```

#### Example
Create 2 files `Dockerfile`, and `main.go`.
Running on bash this command `ls`
```bash
$ ls
Dockerfile
main.go
```

`main.go` has this content
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello from Container!")
}
```

`Dockerfile` has this content:
```docker
FROM golang
WORKDIR /app
COPY . /app
RUN go build -o program main.go
CMD ["./app/program"]
```
> Important: Your docker file must named `Dockerfile`(fist letter on Uppercase). This improtant if you use command `docker build .`. Otherwise if you named any name you must run with `-f`. Example `docker build -f {DOCKERFILE}`.

### Build Image
After create docker file you must build image. 
```bash
# Seek "Dockerfile" and build image with instruction in file
$ docker build .
```
if you have problem build, try to download image wich writed on parametr `FROM` in `Dockerfile`. For Download this image run `docker pull {IMAGE}`. 

Example: By default downloads latest version of golang image
`docker pull golang`

For watch your image, run this command `docer images`.
```bash
$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
<none>       <none>    f05ff1a74e28   6 seconds ago   943MB
```

To remove image run command `docker image rm {IMAGE ID or TAG}`
```bash
$ docker image rm f05ff1a74e28
```

### Create and Run container
After create image must create container with this image. 

1. First we must watch created image with command `docer images` or `docker image ls`
```bash
$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
<none>       <none>    f05ff1a74e28   6 seconds ago   943MB
```
2. Second build container with image `ID` or `TAG`. We will use `Image ID` cause our image haven't `TAG`. (Usage: `docker run {Image ID or TAG }`)
```
$ docker run f05ff1a74e28
Hello from Container!
```

Now our container worked, and now its turned off. And when check your runing containers with comamnd `docker container ps` you will see nothing.
```bash
$ docker container ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
if your container running, use command `docker container stop {Container ID}`

Let's check all containers with command `docker container ps -a` 
```
$ docker container ps -a
CONTAINER ID   IMAGE          COMMAND            CREATED         STATUS                     PORTS     NAMES
f8a26e0cd4d4   f05ff1a74e28   "go run main.go"   2 minutes ago   Exited (0) 1 minutes ago             laughing_murdock
```
Now we see our container wich has worked 1 minutes ago.

For restart this container run command `docker container start {CONTAINER ID or NAME}`
```
$ docker container start -ai laughing_murdock
Hello my friend
```
`-a` - Attach STDOUT/STDERR and forward signals. (Shows to your console output of program) 
`-i` -  Attach container's STDIN. (You write to container runned console)

To Remove containers run command `docker container rm {CONTAINER ID or NAME}`
```bash
$ docker container rm laughing_murdock
```
and on check all containers you will no see the container `laughing_murdock`
```bash
$ docker container ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
> for remove image read it on previous step

# More detailed 
## Docker image

## Docker container

## Docker volumes

