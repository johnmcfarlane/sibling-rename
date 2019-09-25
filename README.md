# Directory Normalisation Bug

## Description
 
When file is renamed and `#include` directives in other files are updated,
their paths are normalised, removing relative paths that contain "`..`".

## Repro

1. Load this project into any version of CLion I can think of, e.g. 2019.3 EAP
   or 2019.2.
1. Observe that *b/h2.h* is included in *a/h1.h* as follows:

   ```c++
   #include "../b/h2.h"
   ```

1. Rename *b/h2.h* to *b/h3.h* using the refactor feature (Refactor->Rename)

1. Observe that *b/h3.h* is included in *a/h1.h* as follows:

   ```c++
   #include "b/h3.h"
   ```

Result: contents of *a/h1.h* is:

```c++
#include "b/h3.h"
```

Expected result: contents of *a/h1.h* is:

```c++
#include "../b/h3.h"
```
