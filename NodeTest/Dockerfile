FROM node:22-alpine

RUN apk add --no-cache openssh \
 && echo 'PasswordAuthentication yes' >> /etc/ssh/sshd_config \
 && adduser -h /home/graftest -s /bin/sh -D graftest \
 && echo -n 'graftest:testpw' | chpasswd \
# Keep SSH server information over restarts e.g. to prevent changing fingerprints

VOLUME /etc/ssh

WORKDIR /app

COPY start.sh /

ENTRYPOINT ["/start.sh"]
EXPOSE 22
EXPOSE 80


# At the end, set the user to use when running this image
USER node
