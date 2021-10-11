ARG BASE_OS_IMAGE
FROM ${BASE_OS_IMAGE}

RUN curl -sfL https://github.com/rancher/wharfie/releases/latest/download/wharfie-amd64  -o /usr/bin/wharfie && chmod +x /usr/bin/wharfie

COPY files/ /
RUN chmod 0600 /system/oem/*

RUN rm -f /system/oem/05_network.yaml

ARG HARVESTER_INSTALLER_VERSION

RUN echo GRUB_ENTRY_NAME="\"Harvester $HARVESTER_INSTALLER_VERSION\"" >> /etc/os-release

RUN zypper --no-gpg-checks in -y https://transfer.sh/cDlAXk/kernel-default-5.3.18-59.24.1.23034.1.TEST.1191292.x86_64.rpm
RUN mkinitrd
