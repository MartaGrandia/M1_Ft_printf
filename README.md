# 🖨️ ft_printf

> A custom reimplementation of the standard C `printf` library function, mastering variadic arguments, base conversions, and low-level buffer formatting.

## 📖 Overview

`ft_printf` is a foundational C programming project focused on building a custom formatted output utility function. The project mimics the core behavior of standard C's `printf()`, parsing format specifiers, handling dynamic variadic parameter lists (`va_list`), converting integers and pointer addresses to string representations (decimal, hex), and writing the output to standard output while accurately tracking the total printed character count.

## ⚙️ Technical Constraints & Architecture

- **Language:** C (compiled with `gcc -Wall -Wextra -Werror`).
- **Output Artifact:** Compiled into a static library archive (`libftprintf.a`) generated via `ar rcs`.
- **Allowed Functions:** `write`, `malloc`, `free`, `va_start`, `va_arg`, `va_copy`, `va_end`.
- **Memory & Return Accuracy:** Zero memory leaks. The function returns the exact total number of characters printed, reproducing system `printf` error/return handling.
- **Standards:** 100% compliant with 42's **Norminette** coding standard.

---

## 🔣 Supported Format Specifiers

The implementation processes format strings sequentially and dispatches variadic parameters based on the following specifiers:

| Specifier | Data Type | Description & Output Format |
| :---: | :--- | :--- |
| `%c` | `char` | Prints a single character. |
| `%s` | `char *` | Prints a null-terminated string (handles `NULL` gracefully). |
| `%p` | `void *` | Prints a pointer memory address in lowercase hexadecimal format (`0x...`). |
| `%d` | `int` | Prints a signed decimal (base 10) number. |
| `%i` | `int` | Prints an integer in base 10. |
| `%u` | `unsigned int` | Prints an unsigned decimal (base 10) number. |
| `%x` | `unsigned int` | Prints a number in lowercase hexadecimal (base 16) format. |
| `%X` | `unsigned int` | Prints a number in uppercase hexadecimal (base 16) format. |
| `%%` | N/A | Prints a literal percent sign (`%`). |

---

## 🛠️ Quickstart & Integration Example

### Usage Example (`main.c`)

You can verify `ft_printf` against standard `printf` by comparing their output side by side:

```c
#include <stdio.h>
#include "ft_printf.h"

int main(void)
{
    int custom_len;
    int std_len;

    // Hexadecimal comparison
    custom_len = ft_printf("Custom ft_printf:  %x\n", 10);
    std_len    = printf("Standard printf:   %x\n", 10);

    printf("Printed chars -> Custom: %d | Standard: %d\n\n", custom_len, std_len);

    // Pointer & Unsigned comparison
    ft_printf("Pointer address: %p\n", &custom_len);
    printf("Pointer address: %p\n", &custom_len);

    return (0);
}

# Clone the repository
git clone [https://github.com/your-username/ft_printf.git](https://github.com/your-username/ft_printf.git)
cd ft_printf

# Compile static library libftprintf.a
make

# Compile test runner against the static library
gcc -Wall -Wextra -Werror main.c libftprintf.a -o printf_test

# Run test binary
./printf_test

# Clean object files and static library
make fclean
