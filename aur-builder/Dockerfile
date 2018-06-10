FROM base/devel

RUN useradd -m -g wheel -s /bin/bash build

RUN mkdir /opt/rippled && chown -R build:wheel /opt/rippled-rpm
RUN echo "%wheel      ALL=(ALL) ALL" >> /etc/sudoers
RUN echo "Defaults:build   !authenticate" >> /etc/sudoers
WORKDIR /opt/rippled

#TODO remove, confirm if taken care of in aur?
#
## RUN git clone https://github.com/ripple/rippled.git
## RUN git clone https://github.com/ripple/validator-keys-tool.git
## COPY rippled.spec ./
## COPY rippled.service /root/rpmbuild/SOURCES/
## COPY 50-rippled.preset /root/rpmbuild/SOURCES/
## COPY update-rippled.sh /root/rpmbuild/SOURCES/
## COPY nofile_limit.conf /root/rpmbuild/SOURCES/
## COPY build_rpm.sh ./
## CMD ./build_rpm.sh

RUN pacman -Syy --noconfirm

# begin build steps
USER build
## aur.sh is a simple script for installing packages from aur
RUN /bin/bash -c '/bin/bash <(curl https://aur.yolk.sh/aur.sh) -s --noconfirm rippled '
# install?
#RUN /bin/bash -c '/bin/bash <(curl https://aur.yolk.sh/aur.sh) -si --noconfirm rippled '
# /end build steps

# todo just run rippled?
#ENTRYPOINT /opt/rippled/pkg/rippled
CMD /bin/bash
