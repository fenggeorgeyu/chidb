# Purpose
This is the forked version of chidb for study/research purpose
Date: 2021/05/04
original repo of chidb: http://chi.cs.uchicago.edu/

# compile

```shell
./autogen.sh
./configure --prefix=${HOME}/.local/
make
```


# problem fix

## include mannually installed `libedit`

Some public development environment may not include `libedit`. You need to first install libedit mannually to your local prefix folder, e.g. `${HOME}/.local` in `include` and `lib` folders.

Then in the source code of chidb in file `Makefile.ac` change:

```shell
#include mannually installed libedit files in ${HOME}/.local/
AM_CFLAGS = -I$(srcdir)/include -I$(srcdir)/src/simclist/ \
            -g3 -Wall -std=gnu99 -ggdb -D_GNU_SOURCE \
            -I${HOME}/.local/include
#don't forget to -ledit
AM_LDFLAGS = -L${HOME}/.local/lib -ledit
```

Then run `authgen.sh` and follow the normal installation procedure.

