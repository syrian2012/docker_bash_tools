# docker_bash_tools
add more tools to your bash make docker easier and faster

# how it works
simply edit your .bashrc file inside your home directory and copy content of code to add in .bashrc file inside it or simply run the follwing it will do the job for you:<br>
cat code_in_bashrc >> ~/.bashrc

to take function you need to logout and login again or start a new shell

don't forget to add your user as a docker admin to avoid problems with running the tools

her what should it function

# List running containers
alias dps='docker ps | less'

# Remove docker image/s
alias drmi='docker rmi'

# List docker images
alias dimgs='docker images'

# Use composer to create container/s
alias dup='docker compose up -d'

# Use composer to stop and delete container/s
alias ddwon='docker compose down'

# build docker image from dockerfile
alias db='docker build .'

# Get container id of exiting container
dgrep(){
    docker ps -a | grep "$1" | cut -c1-12 | head -n 1 
}

# bash into an existing container
dbash() {
    docker exec -ti $(dgrep "$1") /bin/bash
}

# sh into an existing container
dsh() {
    docker exec -ti $(dgrep "$1") /bin/sh
}

# Execute something in an existing container
dex() {
    docker exec -ti $(dgrep "$1") $2
}

# Start an existing container
dstart(){
    docker start $(dgrep "$1")
}

# Restart an existing container
drestart(){
    docker restart $(dgrep "$1")
}

# Stop an existing container
dstop(){
    docker stop $(dgrep "$1")
}

# Remove an existing container
drm(){
    docker rm $(dgrep "$1")
}

# Stop and remove an existing container
dsrm(){
    dstop $(dgrep "$1") && drm $(dgrep "$1")
}

# Get logs of an existing container
dlog(){
    docker logs $(dgrep "$1")
}

after that logout and login again to your shell and all of the above will be functional

enjoy
