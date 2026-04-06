sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
sudo systemctl start docker && sudo systemctl enable docker && sudo usermod -aG docker ec2-user
systemctl status docker


lsblk
sudo growpart /dev/nvme0n1 4
sudo lvextend -L +30G /dev/RootVG/varVol
sudo xfs_growfs /var

<!-- sudo lvextend -L +20G /dev/RootVG/rootVol -->
<!-- sudo xfs_growfs / -->


workstation
===========
1. Install docker -> build the images, push the images to ECR repo hub
2. eksctl -> create, update and delete the eks cluster
3. kubectl -> connect with eks cluster
4. aws cli (aws configure) -> to provide authentication while creating cluster, connecting to cluster


sudo growpart /dev/nvme0n1 4
sudo lvextend -L +30G /dev/RootVG/varVol
sudo xfs_growfs /var

sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ec2-user

# for ARM systems, set ARCH to: `arm64`, `armv6` or `armv7`
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH

curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"

# (Optional) Verify checksum
curl -sL "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_checksums.txt" | grep $PLATFORM | sha256sum --check

tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz

sudo install -m 0755 /tmp/eksctl /usr/local/bin && rm /tmp/eksctl


curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.35.2/2026-02-27/bin/linux/amd64/kubectl
chmod +x ./kubectl
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$HOME/bin:$PATH

eksctl create cluster --config-file=eks.yaml

docker ps
docker images
docker ps -a

docker pull nginx
docker create nginx
docker start 78

docker run nginx

docker rm e5
docker rm 78
docker rm -f 78

docker run -p 8080:80 nginx
docker run -d -p 8080:80 nginx
docker run -d --name myng nginx
docker stats
docker inspect 35



docker login -u username and password

docker build -t prasanthreddymps/myfirstimage:1.0.0 .

docker tag myfirstimage:1.0.0 rasanthreddymps/myimage:1.0.0

docker push prasanthreddymps/myfirstimage:1.0.0

FROM

RUN = install, config packages , at the time of building the image.

CMD = to run the container, executed at the time of running the container,
    will not execute at build time. We can have multiple RUN instructions but only one CMD instruction

LABEL = adds meta data to an image, used for filtering.

    docker images --filter "label=COURSE=Docker"
    docker inspect imagename

EXPOSE = useful to display the port information

ENV = to provide env variables to the containers, app code can access these env variables and use them.
    docker exec -it containerid bash
    env

    docker ps -a -q
    docker rm -f `docker ps -a -q`

COPY = to copy files
    docker build -t copy:1.0.0 .
    docker run -d -p 80:80 copy:1.0.0
    docker ps


ADD = same as copy but it also has capability to fetch from internet and untar the content into image.

ENTRYPOINT = it is used to provide the command executed by the container when it is started


Never run container with root access

USER

WORKDIR

ARG =
    ARG vs ENV
    
    ENV to provide variables to container, can be accessed inside container.
    
    ARG to provide variables to image, and can't be accessed inside container, only accessible at the
    time of building.

    ARG can be first instruction to supply base image.
        # docker build -t arg:1.0.0 --build-arg version=9

ONBUILD =







