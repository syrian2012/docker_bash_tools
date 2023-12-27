# docker_bash_tools
add more tools to your bash make docker easier and faster.
In version 2, you can now select from multiple containers that share the same characters in their names.

# how it works
simply edit your .bashrc file inside your home directory and copy content of code to add in .bashrc file inside it or simply run the follwing it will do the job for you:<br>
cat code_in_bashrc >> ~/.bashrc

to take function you need to logout and login again or start a new shell

don't forget to add your user as a docker admin to avoid problems with running the tools

her what should it function

# dps:
List running containers

# drmi:
Remove docker image/s

# dimgs:
List docker images

# dup:
Use composer to create container/s = 'docker compose up -d'

# ddown:
Use composer to stop and delete container/s = 'docker compose down'

# db:
build docker image from dockerfile = 'docker build .'

# dgrep:
Get container id and name of exiting containers

# dbash container_name:
bash into container

# sh container_name:
sh into container

# dex container_name:
Execute something in container

# dstart container_name:
Start container

# drestart container_name:
Restart container

# dstop container_name:
Stop container

# drm container_name:
Remove container

# dsrm container_name:
Stop and remove container

# dlog container_name:
Get logs of container

# dlogc container_name:
Clear the logs of container

# dinspect container_name:
Inspect container

after that logout and login again to your shell and all of the above will be functional

enjoy
