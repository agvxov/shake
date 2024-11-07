# Shake
SHell mAKE

NOTE:
`shake` has been depricated by `bake`.
`@COMPILECMD` has been replaced by `@BAKE`.
The bake repository tracks the most up to date
versions of all implementations.

Bake mirrors:
* [github](https://github.com/emilwilliams/bake)
* [onion](https://bis64wqhh3louusbd45iyj76kmn4rzw5ysawyan5bkxwyzihj67c5lid.onion/emil/bake)

```
Usage: ./shake <input_file>
	./skake runs the value of @COMPILECMD.
	The value of @COMPILECMD is read from <input_file> in is whatever comes after '@COMPILECMD ' until the end of the line.
	Inside the value of @COMPILECMD all mentions of '$@' are replaced with <input_file>.
	The point of this script is ease to compialation of singe source file (toy) programs.
```

### Rationale
I make many example/test files,
many require linking and trying to remember
which libraries are dependencies
and copying the right command from the source file gets old,
fast.

### Example
```C
$ cat test/hw.c
// @COMPILECMD gcc $@ -o hw.out
#include <stdio.h>

void main(){
		puts("Hello world");
}
$ ./shake test/hw.c
$ ./hw.out
Hello world
```
