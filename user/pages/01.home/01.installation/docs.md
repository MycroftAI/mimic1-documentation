---
title: Installation
taxonomy:
    category:
        - docs
---

Obtain copy of the git repo:

```
git clone https://github.com/MycroftAI/mimic.git
```

## Linux 

#### Requirements

```
make 

gcc

libasound2-dev (ubuntu)
```

#### Compilation Instructions

Navigate to the mimic directory:

```
cd mimic
```

Setup configuration files for your machine:

```
./configure
```

Build mimic:

```
make
```

>>>>> When rebuilding, often you will only need to run `make`.
If you make changes to compile flags you will probably want to
run `make clean` before recompiling with `make`.
