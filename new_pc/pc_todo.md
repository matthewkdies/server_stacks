# PC Parts

- [ ] [Bundle](https://www.microcenter.com/product/5006968/amd-ryzen-7-7700x,-gigabyte-b650-gaming-x-ax-v2,-gskill-flare-x5-series-32gb-ddr5-6000-kit,-computer-build-bundle)
- [ ] Power supply (fully modular)
- [ ] Case
- [ ] SSD
- [ ] Cables
- [ ] Cooling (?)

# Associated Movement Info

- [ ] Firewall
    - [ ] The below proposed network changes will need updates such that they're all reachable securely
- [ ] Secure user creation
    - [ ] Create a user/group specifically for running the containers

# Container Updates

- [ ] Rethink networking
    - [ ] Rather than everything being on a single bridge network, each should have their own network, where possible
- [ ] Reverse proxy: caddy, not traefik
    - [ ] Integrate with authelia
- [ ] Security improvements
    - [ ] Use secrets, where possible
    - [ ] `security_opt`
- [ ] Resource improvements
    - [ ] Memory and CPU limits
- [ ] Healthchecks