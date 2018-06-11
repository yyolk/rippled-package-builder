FROM base/devel

RUN useradd -m -g wheel -s /bin/bash build

ENV BUILD_DIR /opt/rippled
RUN mkdir $BUILD_DIR && \
    chown -R build:wheel $BUILD_DIR && \
    echo "%wheel      ALL=(ALL) ALL" >> /etc/sudoers && \
    echo "Defaults:build   !authenticate" >> /etc/sudoers 
#%wheel ALL=(ALL) NOPASSWD: ALL
WORKDIR $BUILD_DIR

#TODO remove, confirm if taken care of in aur?
## RUN git clone https://github.com/ripple/rippled.git
## RUN git clone https://github.com/ripple/validator-keys-tool.git
## COPY rippled.spec ./
## COPY rippled.service /root/rpmbuild/SOURCES/
## COPY 50-rippled.preset /root/rpmbuild/SOURCES/
## COPY update-rippled.sh /root/rpmbuild/SOURCES/
## COPY nofile_limit.conf /root/rpmbuild/SOURCES/
## COPY build_rpm.sh ./
## CMD ./build_rpm.sh

RUN pacman -Syy git --noconfirm

# begin build steps
USER build
# get past failing check() in PKGBUILD
RUN git clone https://github.com/yyolk/aur-rippled.git /opt/rippled/rippled
WORKDIR $BUILD_DIR/rippled
RUN makepkg -s --noconfirm
# install?
## aur.sh is a simple script for installing packages from aur
#RUN /bin/bash -c '/bin/bash <(curl https://aur.yolk.sh/aur.sh) -si --noconfirm rippled '
# /end build steps

# todo just run rippled?
#ENTRYPOINT /opt/rippled/pkg/rippled
CMD /bin/bash
