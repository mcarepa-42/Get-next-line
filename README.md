# Get Next Line

`get_next_line` is a 42 project that implements a function capable of reading one line at a time from a file descriptor.

It is useful for reading files, standard input, pipes, or any other valid file descriptor line by line.

## How to download

Clone the repository:

```bash
git clone https://github.com/mcarepa-42/Get-next-line.git
cd Get-next-line
```

Or download it from GitHub by clicking **Code** > **Download ZIP**, then extract the ZIP and open a terminal inside the project folder.

## Requirements

You need:

- a C compiler such as `cc`, `gcc`, or `clang`

## How to compile a test

Create a small test file named `main.c`:

```c
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include "get_next_line.h"

int main(void)
{
    int fd;
    char *line;

    fd = open("test.txt", O_RDONLY);
    if (fd < 0)
        return (1);
    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return (0);
}
```

Create a file to read:

```bash
printf "line one\nline two\nline three\n" > test.txt
```

Compile:

```bash
cc -Wall -Wextra -Werror main.c get_next_line.c get_next_line_utils.c -D BUFFER_SIZE=42 -o gnl_test
```

Run:

```bash
./gnl_test
```

## Bonus files

If you want to test the bonus version, compile the bonus files instead:

```bash
cc -Wall -Wextra -Werror main.c get_next_line_bonus.c get_next_line_utils_bonus.c -D BUFFER_SIZE=42 -o gnl_test
```

## Notes

You can change `BUFFER_SIZE` during compilation:

```bash
cc main.c get_next_line.c get_next_line_utils.c -D BUFFER_SIZE=1 -o gnl_test
cc main.c get_next_line.c get_next_line_utils.c -D BUFFER_SIZE=9999 -o gnl_test
```
