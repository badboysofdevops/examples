# Dockerized development environment

This is example of development environment at the Docker container.
It's tested only at Linux.

It installs Microsoft Visual Studio Code, and Ubuntus C/C++ development stuff. When you build your own development environment, you just change what are required for your environment. 

This might be broken if your desktop UID is not 1000. I didn't test that kind of case. If you found there's problem, help us to fix it please. 

## Building

Building is just done with:
docker build -t devenv .

## Running

Running is a bit more complicated. I'm using following script:

docker run -ti -u $UID -v $HOME/src:/workdir -w /workdir -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix devenv

It starts automatically the Code IDE.

### What does it do?

*-u $UID* sets the container user for the same ID as you are. This way you have access to your own files at the host machine
*-v $HOME/src:/workdir* Set's the src directory in your home directory to /workingdir inside the container. When you open the files, you open them from here
*-e DISPLAY=$DISPLAY* Set's the X dispaly ID inside the container to same as you have at the desktop
*-v /tmp/.X11-unix:/tmp/.X11-unix* Imports the sockets and other related and required items from your desktop X to the container. 