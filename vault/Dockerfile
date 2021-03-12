# Imagen Base
FROM alpine:3.11

# Agregamos la Ultima version. 
ENV VAULT_VERSION 1.6.3

# Creacion de Directorio
RUN mkdir /vault

# Descarga de Dependencias
RUN apk --no-cache add \
      bash \
      ca-certificates \
      wget

# Descarga de Vault y Configuracion
RUN wget --quiet --output-document=/tmp/vault.zip https://releases.hashicorp.com/vault/${VAULT_VERSION}/vault_${VAULT_VERSION}_linux_amd64.zip && \
    unzip /tmp/vault.zip -d /vault && \
    rm -f /tmp/vault.zip && \
    chmod +x /vault

# Path
ENV PATH="PATH=$PATH:$PWD/vault"

# Agregar Archivos de Configuracion
COPY ./config/vault-config.json /vault/config/vault-config.json

# Exponemos el Port 8200
EXPOSE 8200

# Run Vault
ENTRYPOINT ["vault"]

