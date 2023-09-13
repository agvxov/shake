# emake
Easy MAKE

	Usage: ./emake <input_file>
		./emake runs the value of @COMPILECMD.
		The value of @COMPILECMD is read from <input_file> in is whatever comes after '@COMPILECMD ' until the end of the line.
		Inside the value of @COMPILECMD all mentions of '$@' are replaced with <input_file>.
		The point of this script is ease to compialation of singe source file (toy) programs.

### Rationale
I make many example/test files, many require linking and trying to remember which libraries are dependencies or copying the right command from the source file gets old fast.

### Example
```sh
	$ cat test/hw.c
```
```C
	// @COMPILECMD gcc $@ -o hw.out
	#include <stdio.h>

	void main(){
			puts("Hello world");
	}
```
```sh
	$ ./emake test/hw.c
	$ ./hw.out
	Hello world
```
