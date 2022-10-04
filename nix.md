# shell environments
`nix-shell -p git neovim curl`

# Links
[Nix weekly](https://weekly.nixos.org/)
[More Tutorials](https://weekly.nixos.org/2021/05-nixos-weekly-2021-05.html)
[hydra](https://github.com/NixOS/hydra) CI service for nix

# Tutorials [->nix.dev](https://nix.dev/)
- install Nix
- Ad hoc developer environment
- towards reproducibility
  - pinning packages with URLs
- declarative and reproducible developer environment
  - `direnv`
- CI with GitHub Actions
- Set up a development environment [->](https://nix.dev/tutorials/dev-environment)
  - [proj2](./proj2) (basic python flask project)
  - Build: `nix-build`, creates symlink _result_
  - Run: `nix-shell default.nix` or `./result/bin/myapp`
  - nix takes the role of _pip_ or _virtualenv_
  - __TODO:__ check out __Flake__! [AltF4Stream setting up a flakefile](https://www.youtube.com/watch?v=oqXWrkvZ59g)
- Building and running Docker images [->](https://nix.dev/tutorials/building-and-running-docker-images)
  - [proj3](./proj3-docker) uses [nixpkgs.dockerTools ->docs](https://nixos.org/manual/nixpkgs/stable/#sec-pkgs-dockerTools)
  - Build: `nix-build; docker load < result` or `docker load < $(nix-build)`
  - Run: `docker run -t hello-docker:cwvsf3n9ks9dgpck3n3ini9pnc550a0w`
  - nix replaces the Dockerfile functionality, so no more Dockerfiles!
  - using Docker CLI, Docker Compose, Docker Swarm or Docker Hub my still be relevant
  - [more examples of Docker images build with Nix](https://github.com/NixOS/nixpkgs/blob/master/pkgs/build-support/docker/examples.nix)
  - [Arion](https://docs.hercules-ci.com/arion/) a docker-compose wrapper with first class support for Nix
- Building a bootable ISO image [->](https://nix.dev/tutorials/building-bootable-iso-image)
- Deploying NixOS using Terraform
  - [terrafrom](~/md/terraform.md)
