---
title: Installation
taxonomy:
    category:
        - docs
---

Obtain copy of the git repo:

```bash
git clone https://github.com/MycroftAI/mimic.git
```

## Linux 

#### Requirements

```bash
make 

gcc

libasound2-dev (ubuntu)
```

#### Compilation Instructions

Navigate to the mimic directory:

```bash
cd mimic
```

Setup configuration files for your machine:

```bash
./configure
```

Build mimic:

```bash
make
```

>>>>> When rebuilding, often you will only need to run `make`.
If you make changes to compile flags you will probobly want to
run `make clean` before recompiling with `make`.