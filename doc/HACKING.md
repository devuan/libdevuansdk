libdevuansdk
------------

## Strings for translation

To support gettext translation use Zuper's functions for noticing messages to console:

 - `notice` (green visible header)
 - `act` (bullet point information)
 - `warning` (orange warning, non fatal)
 - `error` (fatal error) followed by `zerr` and `zshexit`

Each string should not contain any variable, but pointers to
variables, then be followed by actual variables as arguments. So for
instance:

```
notice "Starting to bake files in ::1 directory:: for target ::2 arch::" $dir $arch
```

This will print the string with variables in it, but string will
contain references to them. This is so that gettext translations will
point to the same string even in case of name of variables changing.


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

## Submodule administration

To update all submodules use:

```
git submodule foreach git pull --rebase origin master
```

This will cycle through all submodules and update them to the respective latest HEAD. After this the repository needs to be updated with the reference to this new HEAD with a commit.
