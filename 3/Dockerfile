FROM debian:bookworm

RUN apt update && \
    apt full-upgrade -y && \
    apt autoremove --purge -y && \
    apt install ca-certificates curl wget -y && \
    echo 'deb [signed-by=/usr/share/keyrings/cznic-labs-pkg.gpg] https://pkg.labs.nic.cz/bird3 bookworm main' > /etc/apt/sources.list.d/cznic-labs-bird3.list && \
    wget -O /usr/share/keyrings/cznic-labs-pkg.gpg https://pkg.labs.nic.cz/gpg && \
    apt update && \
    apt install bird3 -y && \
    apt autoremove --purge -y && \
    rm -rf /var/lib/apt/lists/* && \
    rm -f /etc/bird/envvars && \
    mkdir /run/bird && \
    chown root:root /etc/bird && \
    find /etc/bird -type d -exec chmod 0700 {} \; && \
    find /etc/bird -type f -exec chmod 0600 {} \;

ENTRYPOINT ["bird"]
CMD ["-f"]
