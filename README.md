# compilers-docker
Instructions for a Docker image for the Stanford Compiler MOOC

## Running

Effectively, you'll run all the commands that would be in the virtual machine
within the context of a docker image. For example, to create the second
assignment (C++ version), the instructions say to run:

```
make -f /usr/class/cs143/assignments/PA3/Makefile
```

Within the Docker context, you'd run this instead:

```
docker run --rm -it -v $PWD:/workspace cmc333333/compilers-docker \
  make -f /usr/class/cs143/assignments/PA3/Makefile
```

As the first bit is a mouth-full, I recommend using a variable or alias
instead:

```
COMP="docker run --rm -it -v $PWD:/workspace cmc333333/compilers-docker"

# Later
$COMP make -f /usr/class/cs143/assignments/PA3/Makefile
```

## File Ownership
Most of the course commands copy several files from the provided image into
the local directory, but using the root user. To modify them, you may need to
change their ownership, e.g.

```
sudo chown $USER:$USER -R .
```

Then you can edit the files in whatever text editors/IDEs you'd like.
