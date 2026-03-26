# almalinux is same as redhat image
FROM almalinux:9
RUN dnf install nginx -y
# CMD ["nginx","-g", "daemon off;"]

# root access required to create user
RUN useradd roboshop


# change root user to created user
USER roboshop
CMD ["sleep", "100"]

