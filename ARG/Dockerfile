# almalinux is same as redhat image
ARG version
# defaults to 8 if not override
FROM almalinux:${version:-8}

# docker build -t arg:1.0.0 --build-arg version=9

ARG COURSE="DOcker" \
      TRAINER="Siva" \
      AUTHOR-="JoinDevOps"

RUN echo "Trainer is: ${TRAINER}, version is: ${version}"
CMD ["sleep", "200"]

