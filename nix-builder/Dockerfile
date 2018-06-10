FROM nixos/nix:latest

RUN nix-channel --add https://nixos.org/channels/nixpkgs-unstable nixpkgs
RUN nix-channel --update

ENV BASE_PACKAGES 'boost openssl protobuf gcc-unwrapped libstdcxx5 gitAndTools.gitFull zlib cmake wget which gnupg'
RUN nix-build -A boost '<nixpkgs>'
RUN nix-build -A openssl '<nixpkgs>'
RUN nix-build -A protobuf '<nixpkgs>'
RUN nix-build -A gcc-unwrapped '<nixpkgs>'
#fails
#RUN nix-build -A libstdcxx5 '<nixpkgs>'
RUN nix-build -A gitAndTools.gitFull '<nixpkgs>'
RUN nix-build -A zlib '<nixpkgs>'
RUN nix-build -A cmake '<nixpkgs>'
RUN nix-build -A wget '<nixpkgs>'
RUN nix-build -A which '<nixpkgs>'
RUN nix-build -A gnupg '<nixpkgs>'
