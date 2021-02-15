# Create the Nginx production ingress proxy image.
ARG REGISTRY=""
ARG REPOSITORY=""
FROM ${REGISTRY}${REPOSITORY}golden-nginx:latest AS ingress-proxy-production

ARG BUILD_TAG=local
LABEL build_tag=${BUILD_TAG}
LABEL description="My Production Ingress Proxy"

# Copy the certificates.
COPY ./nginx/certs /etc/nginx/certs/
# Protect any private keys.
RUN chmod 400 /etc/nginx/certs/*.key
# Copy the site specific Nginx production configuration files.
COPY ./nginx/conf.d /etc/nginx/conf.d/