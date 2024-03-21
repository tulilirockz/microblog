+++
title = "Niche Software and Nix (or Guix, or anything deterministic)"
author = "Tulip"
date = "2024-03-20"
description = "A post talking about me and Nix!"
categories = [
    "Tech Stuff"
]
tags = [
    "Me",
    "Nix"
]
+++

Honestly its been quite a while since I've written anything about anything, and honestly that was mostly because I didnt know exactly what to write about, but now, a lot of stuff has changed in my life and I have a bunch more stuff to talk about. Most likely going to write a lot more from now on!


### Well, what is up with Nix?

[Nix](https://nixos.org/) is an AMAZING piece of software, honestly! People talked about it like it was just a tech demo or something but it has proven itself to be quite reliable, and thats honestly amazing. It uses a very deterministic package managing system, without OSTree or anything like that, because it uses a very weird way of storing packages, but it is still amazing. It basically can reproduce any kind of system on any kind of configuration on anything really, it even more portable than Runc or ContainerD runtimes honestly, since it can reproduce any kind of dependency without conflicting with anything.

### What kind of enviroment can I even get running then?

Anything. Quite literally anything! Nix can run ANYTHING at any time at any moment. You can build [virtual machines, remote desktop enviroments](https://github.com/MatthewCroughan/NixThePlanet) \(with VNC or RDP or anything you want\), [OCI images](https://nix.dev/tutorials/nixos/building-and-running-docker-images.html), and even build stuff like [DEB or RPM](https://nixos.wiki/wiki/Nixpkgs/Building_RPM_DEB_with_nixpkgs) packages! Its wonderful for packaging everything, it has integration with a bunch of development utilities, like [pre-commit](https://github.com/cachix/pre-commit-hooks.nix), and the [FlakeHub CLI](https://github.com/DeterminateSystems/fh) helps you out setting up your project for anything, nodejs, rust, go, whatever you throw at it!

### Nix is cool, but what are you even trying to say?

Well, I really just wanted to express how happy I am for nix existing and how glad people actually work with this tool, it has helped me out A LOT with my setup (which I will link here). And Im not only exited for nix tho, even stuff like Guix, or really anything properly deterministic, like Cargo and the Crates.io packaging system is amazing, since itll let my software live on forever as long as all the dependencies still exist!

### Other stuff

Im also trying to help out the nix ecossystem by packaging many different projects in nix packages! Like [Bluebuild], [Flameshow], and others! If you have any interest in helping with nix and want to see the ecossystem flourish, please make sure to package your favourite project in a nix package, im sure people will appreciate! FlakeHub CLI makes it SUPER easy to get started and I recommend you to add your flake to FlakeHub for discoverability! 


I know this doesnt have anything to do with Nix, but make sure to check out [Systemd-MachineD and their nspawn utility](https://github.com/nspawn/nspawn)! They are extensively used in NixOS to host guest NixOS instances, and it is an amazing project also. I even made an [unofficial flake](https://github.com/tulilirockz/nspawn-flake) of their things! They have an awesome registry on [nspawn.org](https://nspawn.org/)
