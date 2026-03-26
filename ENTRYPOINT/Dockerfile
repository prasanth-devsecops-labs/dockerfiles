FROM almalinux:9

# CMD ["ping","google.com"]
# docker run imagename ping facebook.com, CMD command can be override in run time

# ENTRYPOINT [ "ping","google.com" ]
# docker run imagename ping facebook.com
    # ping google.com ping facebook.com >> appends, we can't override entrypoint command.
# docker ps -a --no-trunc

# best results we can mix both CMD provides default input args to ENTRYPOINT
CMD ["google.com"]
ENTRYPOINT ["ping"]

