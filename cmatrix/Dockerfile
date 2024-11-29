FROM alpine
LABEL org.opencontainers.image.authors="Eduardo Flores"
LABEL org.opencontainers.image.description="Container image for https://github.com/abishekvashok/cmatrix"

WORKDIR /root/cmatrix
# Actualiza y añade dependencias necesarias
RUN apk update && \
    apk add git autoconf automake alpine-sdk ncurses-dev ncurses-static

# Clona el repositorio y compila cmatrix
WORKDIR /root
RUN git clone https://github.com/eduflornet/cmatrix.git && \
    cd cmatrix && \
    autoreconf -i && \
    ./configure LDFLAGS="-static" && \
    mkdir -p /usr/lib/kbd/consolefonts /usr/share/consoletrans && \
    make

# Establece el comando por defecto
CMD ["./cmatrix/cmatrix"]





