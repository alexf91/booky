# Booky

A simple bookmark manager for the command line.

There are several more powerful alternatives, but it's not always possible to
install them. Booky is contained in a single Python file and only depends
on the Python standard library.

## Setup

To be able to change directories, a wrapper function around Booky is required.

### bash and zsh

```bash
function bookyrs {
    # Restore a directory from booky
    if [ $# != 1 ]; then
        return 1
    fi

    DIR=$(booky get $1)
    if [ $? != 0 ]; then
        return 1
    fi

    cd $DIR
}

function bookysv {
    # The current directory to booky
    if [ $# != 1 ]; then
        return 1
    fi

    booky add $1
}
```

## Notes

The bookmarks file is not locked, so simultaneous reading and writing results
in undefined behavior.
