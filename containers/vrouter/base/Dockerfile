ARG CONTRAIL_REGISTRY
ARG CONTRAIL_CONTAINER_TAG
FROM ${CONTRAIL_REGISTRY}/contrail-base:${CONTRAIL_CONTAINER_TAG}

# removing network-scripts: this folder will mounted from the host (or not used in Ubuntu) so the one installed by initscripts package in container is removed.

RUN yum install -y initscripts ethtool pciutils sudo contrail-vrouter-utils && \
    ldconfig && \
    rm -rf /etc/sysconfig/network-scripts

COPY *.sh ifup-* ifdown-* network-functions-vrouter* /

ENV NODE_TYPE=vrouter
LABEL net.juniper.contrail.pod=$NODE_TYPE
CMD ["/usr/bin/tail","-f","/dev/null"]
