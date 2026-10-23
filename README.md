<div align="center">

# libft

**A from-scratch C library of essential utilities — strings, memory, numbers, I/O and linked lists — written in C and written to the strict 42 School Norm.**

[![C](https://img.shields.io/badge/C-Library-0052B4?style=flat)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Makefile](https://img.shields.io/badge/Makefile-Build-E8115B?style=flat)](https://www.gnu.org/software/make/)
[![42](https://img.shields.io/badge/42-Norm-111111?style=flat)](https://github.com/42School/norm)

**44 functions · from scratch · static library · zero dependencies**

</div>

---

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [API Reference](#api-reference)
4. [Requirements](#requirements)
5. [Getting Started](#getting-started)
6. [Usage](#usage)
7. [Project Structure](#project-structure)
8. [Author](#author)

---

## Overview

**libft** is a self-contained, from-scratch C library that implements the utility functions every C developer needs when building larger programs:

- **String manipulation** — length, copying, concatenation, comparison, searching, splitting and mapping
- **Memory management** — allocation, zeroing, copying and comparison with overlap safety
- **Character classification & conversion** — alpha, digit, alnum, ascii, print and upper/lower casing
- **Numeric conversion** — string to integer parsing with sign handling and overflow protection
- **File-descriptor I/O** — character, string, line and number output to any file descriptor
- **Linked lists** — a modern `t_list` implementation: creation, traversal, iteration and mapping

Every function is implemented by hand in plain C, without external dependencies or platform-specific APIs, and is compiled into a static library (`libft.a`) whose public interface lives in [`libft.h`](libft.h).

The project follows the conventions of the [42 School](https://www.42school.com/) curriculum, including the mandatory header comment block and coding standards required by the [42 Norm](https://github.com/42School/norm).

## Features

### String Manipulation

| Function | Description |
| --- | --- |
| `ft_strlen` | Returns the length of a string, excluding the null terminator |
| `ft_strlcpy` | Safely copies a string into a bounded buffer, returning the total length |
| `ft_strlcat` | Safely appends a string to a bounded buffer, returning the total length |
| `ft_strchr` | Finds the first occurrence of a character in a string (null-aware) |
| `ft_strrchr` | Finds the last occurrence of a character in a string (null-aware) |
| `ft_strncmp` | Compares at most `n` characters of two strings |
| `ft_strnstr` | Finds a substring within the first `n` characters of a haystack |
| `ft_strdup` | Duplicates an existing string |
| `ft_substr` | Extracts a substring from a string |
| `ft_strjoin` | Joins two strings into a new string |
| `ft_strtrim` | Trims characters from the start and end of a string |
| `ft_split` | Splits a string into an array of words |
| `ft_strmapi` | Applies a function to each character of a string and builds a new string |
| `ft_striteri` | Applies a function to each character of a string in place |
| `ft_itoa` | Converts an integer to its string representation |

### Memory Management

| Function | Description |
| --- | --- |
| `ft_memset` | Fills the first `n` bytes of a buffer with a given value |
| `ft_bzero` | Zeroes the first `n` bytes of a buffer (for buffers that must not contain pointers) |
| `ft_memcpy` | Copies `n` bytes from one buffer to another |
| `ft_memmove` | Moves `n` bytes between buffers, safely handling overlap |
| `ft_calloc` | Allocates and zero-initializes `n` elements of `size` bytes |
| `ft_memchr` | Finds the first occurrence of a byte in a buffer |
| `ft_memcmp` | Compares `n` bytes between two buffers |

### Character Classification & Conversion

| Function | Description |
| --- | --- |
| `ft_isalpha` | Checks whether a character is an alphabetic letter |
| `ft_isdigit` | Checks whether a character is a digit |
| `ft_isalnum` | Checks whether a character is alphanumeric |
| `ft_isascii` | Checks whether a character is an ASCII character |
| `ft_isprint` | Checks whether a character is printable |
| `ft_toupper` | Converts a lowercase character to uppercase |
| `ft_tolower` | Converts an uppercase character to lowercase |

### Numeric Conversion

| Function | Description |
| --- | --- |
| `ft_atoi` | Converts a null-terminated numeric string into an integer, with sign and overflow handling |

### File-Descriptor I/O

| Function | Description |
| --- | --- |
| `ft_putchar_fd` | Writes a single character to a file descriptor |
| `ft_putstr_fd` | Writes a string to a file descriptor |
| `ft_putendl_fd` | Writes a string followed by a newline to a file descriptor |
| `ft_putnbr_fd` | Writes an integer to a file descriptor |

### Linked Lists

| Function | Description |
| --- | --- |
| `ft_lstnew` | Creates a new linked list node |
| `ft_lstadd_front` | Prepends a node to a list |
| `ft_lstadd_back` | Appends a node to a list |
| `ft_lstdelone` | Unlinks and deletes a node without freeing the whole list |
| `ft_lstclear` | Deletes and frees every node of a list |
| `ft_lstiter` | Applies a function to every node content in a list |
| `ft_lstmap` | Builds a new list by applying a function to every node content |
| `ft_lstsize` | Returns the number of nodes in a list |
| `ft_lstlast` | Returns the last node of a list |

## API Reference

### String Functions

```c
size_t  ft_strlen(const char *s);
char    *ft_strchr(const char *s, int c);
char    *ft_strrchr(const char *s, int c);
int     ft_strncmp(const char *s1, const char *s2, size_t n);
char    *ft_strnstr(const char *h, const char *n, size_t len);
char    *ft_strdup(const char *s);
char    *ft_substr(char const *s, unsigned int start, size_t len);
char    *ft_strjoin(char const *s1, char const *s2);
char    *ft_strtrim(char const *s1, char const *set);
char    **ft_split(char const *s, char c);
char    *ft_strmapi(char const *s, char (*f)(unsigned int, char));
void    ft_striteri(char *s, void (*f)(unsigned int, char *));
char    *ft_itoa(int n);
size_t  ft_strlcpy(char *dst, const char *src, size_t dstsize);
size_t  ft_strlcat(char *dst, const char *src, size_t dstsize);
```

### Memory Functions

```c
void    *ft_memset(void *b, int c, size_t len);
void    *ft_bzero(void *s, size_t n);
void    *ft_memcpy(void *dst, const void *src, size_t n);
void    *ft_memmove(void *dst, const void *src, size_t len);
void    *ft_calloc(size_t count, size_t size);
void    *ft_memchr(const void *s, int c, size_t n);
int     ft_memcmp(const void *s1, const void *s2, size_t n);
```

### Character Functions

```c
int     ft_isalpha(int c);
int     ft_isdigit(int c);
int     ft_isalnum(int c);
int     ft_isascii(int c);
int     ft_isprint(int c);
int     ft_toupper(int c);
int     ft_tolower(int c);
int     ft_atoi(const char *str);
```

### I/O Functions

```c
void    ft_putchar_fd(char c, int fd);
void    ft_putstr_fd(char *s, int fd);
void    ft_putendl_fd(char *s, int fd);
void    ft_putnbr_fd(int n, int fd);
```

### Linked List Functions

```c
typedef struct s_list {
    void *content;
    struct s_list *next;
} t_list;

t_list  *ft_lstnew(void *content);
void    ft_lstadd_front(t_list **lst, t_list *new);
int     ft_lstsize(t_list *lst);
t_list  *ft_lstlast(t_list *lst);
void    ft_lstadd_back(t_list **lst, t_list *new);
void    ft_lstdelone(t_list *lst, void (*del)(void *));
void    ft_lstclear(t_list **lst, void (*del)(void *));
void    ft_lstiter(t_list *lst, void (*f)(void *));
t_list  *ft_lstmap(t_list *lst, void *(*f)(void *), void (*del)(void *));
```

## Requirements

- A C compiler: `gcc` or `clang`
- GNU `make`
- [norminette](https://github.com/42School/norm) — optional, for checking 42 Norm compliance

## Getting Started

### Prerequisites

Make sure a C compiler and `make` are installed on your machine:

```bash
gcc --version   # or: clang --version
make --version
```

### Installation

Clone the repository and build the static library:

```bash
git clone https://github.com/<github-user>/libft.git
cd libft
make
```

The build produces a static library named `libft.a` in the project root.

### Available Makefile Targets

| Target | Description |
| --- | --- |
| `all` | Build the static library (`libft.a`) |
| `clean` | Remove all object files |
| `fclean` | Remove all object files and the static library |
| `re` | Perform a full rebuild (`fclean` + `all`) |

## Usage

Once built, link against the library in your own projects:

```bash
gcc -Wall -Wextra -Werror -I. your_program.c libft.a -o your_program
```

```c
#include <stdlib.h>
#include <unistd.h>

#include "libft.h"

int main(void)
{
	char *greeting;

	greeting = ft_strjoin("Hello, ", "world!");
	if (!greeting)
		return (1);
	ft_putstr_fd(greeting, 1);
	ft_putendl_fd("", 1);
	free(greeting);

	ft_putstr_fd("Answer: ", 1);
	ft_putnbr_fd(ft_atoi("1337"), 1);
	ft_putchar_fd('\n', 1);
	return (0);
}
```

## Project Structure

```
libft/
├── ft_*.c        # Library implementation files (one per function group)
├── libft.h       # Public header: shared types and function prototypes
├── Makefile      # Build system producing libft.a
└── README.md     # Project documentation
```

## Author

**yassir** — 42 School · `yassir@student.1337.ma`

## License

`libft` is an educational project of the 42 School curriculum. It is provided for learning and development purposes.
