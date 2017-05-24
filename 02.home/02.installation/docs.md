---
title: Build
taxonomy:
    category:
        - docs
---

## Build

### On a native build (not cross-compilation)

- Clone the repository
  ```
  $ git clone https://github.com/MycroftAI/mimic.git
  ```
  
- Navigate to mimic directory
  ```
  $ cd mimic
  ```

- Generate build scripts
  ```
  $ ./autogen.sh
  ```
  
- Configure.

  ```
  $ ./configure --prefix="/usr/local"
  ```
  
- Build
  ```
  $ make
  ```
  
- Check
  ```
  $ make check
  ```

### Cross compilation:

- Run the windows build script:

```
./run_testsuite.sh winbuild
```

- Test it: The directory `install` will contain `bin/mimic.exe` file

```
wine ./mimic.exe -t "hello world" 
```

- Distribute it

You can distribute the compiled mimic by adding to a zip file everything in the
`install/winbuild/bin` directory.


>>>>> When rebuilding, often you will only need to run `make`.
If you make changes to compile flags you will probobly want to
run `make clean` before recompiling with `make`.
