FROM alpine:latest

ARG VCS_REF=master
ARG BUILD_DATE=""
ARG REGISTRY_PATH=paritytech
ARG TERRAFORM_VERSION

# metadata
LABEL io.parity.image.authors="devops-team@parity.io" \
	io.parity.image.vendor="Parity Technologies" \
	io.parity.image.title="${REGISTRY_PATH}/terraform" \
	io.parity.image.description="ca-certificates git jq make curl gettext; terraform;" \
	io.parity.image.source="https://github.com/paritytech/scripts/blob/${VCS_REF}/\
dockerfiles/terraform/Dockerfile" \
	io.parity.image.documentation="https://github.com/paritytech/scripts/blob/${VCS_REF}/\
dockerfiles/terraform/README.md" \
	io.parity.image.revision="${VCS_REF}" \
	io.parity.image.created="${BUILD_DATE}"

RUN apk add --no-cache \
		ca-certificates git jq make curl gettext; \
	curl "https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip" \
		-o terraform.zip; \
	unzip terraform.zip	-d /usr/local/bin/ terraform; \
	rm terraform.zip; \
	chmod +x /usr/local/bin/terraform

WORKDIR /config

CMD ["/bin/sh"]
