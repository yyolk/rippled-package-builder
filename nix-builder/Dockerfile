FROM nixos/nix:latest

RUN nix-channel --add https://nixos.org/channels/nixpkgs-unstable nixpkgs
RUN nix-channel --update

#RUN nix-build -A  '<nixpkgs>'
RUN nix-env -iA nixos.boost
