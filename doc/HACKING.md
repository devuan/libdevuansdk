libdevuansdk
------------

## Code style

### Leading whitespace
* Use tabs for indentation
* Use spaces for alignment
	* This means no tabs except beginning of line
	* Everything will line up independent of tab size

### Variable naming
* Do not name your variables UPPERCASE unless they are environment related.
* All variables local to the project should stay lowercase

### Function naming
* Use underscores, not dashes in naming.
* Declare every function with `fn function_name` for zuper.
* Sort all functions alphabetically in their respective files.
	* Write its needed documentation in `doc/README-functions.md`

### Other
* No files chmodded to +x. This is a library.

## Workflow

libdevuansdk is split into three stages. See `doc/WORKFLOW.md` for more info on it.

### Stage 1
* debootstrap (stage 1+2+3)
	* gives you a working system
	* tarball it for later use
	* raw image (dd-ed zeroes)

### Stage 2
* declare entities
* customize system

### Stage 3
* packing
