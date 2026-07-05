# The Norm

Version 4.1

Summary: This document describes the applicable standard (Norm) at 42: a programming standard that defines a set of rules to follow when writing code. The Norm applies to all C projects within the Common Core by default, and to any project where it is specified.

## Contents

- [The Norm](#the-norm)
  - [Contents](#contents)
  - [I. Foreword](#i-foreword)
  - [II. Why?](#ii-why)
  - [III. The Norm](#iii-the-norm)
    - [III.1 Naming](#iii1-naming)
    - [III.2 Formatting](#iii2-formatting)
    - [III.3 Functions](#iii3-functions)
    - [III.4 Typedef, struct, enum and union](#iii4-typedef-struct-enum-and-union)
    - [III.5 Headers - a.k.a include files](#iii5-headers---aka-include-files)
    - [III.6 The 42 header - a.k.a start a file with style](#iii6-the-42-header---aka-start-a-file-with-style)
    - [III.7 Macros and Pre-processors](#iii7-macros-and-pre-processors)
    - [III.8 Forbidden stuff](#iii8-forbidden-stuff)
    - [III.9 Comments](#iii9-comments)
    - [III.10 Files](#iii10-files)
    - [III.11 Makefile](#iii11-makefile)

## I. Foreword

The norminette is a Python and open source code that checks Norm compliance of your source code. It checks many constraints of the Norm, but not all of them (e.g. subjective constraints). Unless specific local regulations on your campus, the norminette prevails during evaluations on the controlled items.

In the following pages, rules that are not checked by the norminette are marked with `(*)`, and can lead to project failure (using the Norm flag) if discovered by the evaluator during a code review.

Its repository is available at <https://github.com/42School/norminette>. Pull requests, suggestions and issues are welcome.

## II. Why?

The Norm has been carefully crafted to fulfill many pedagogical needs. Here are the most important reasons for all the choices below:

- Sequencing: coding implies splitting a big and complex task into a long series of elementary instructions. All these instructions will be executed in sequence: one after another. A beginner that starts creating software needs a simple and clear architecture for their project, with a full understanding of all individual instructions and the precise order of execution. Cryptic language syntaxes that do multiple instructions apparently at the same time are confusing, and functions that try to address multiple tasks mixed in the same portion of code are sources of errors.

  The Norm asks you to create simple pieces of code, where the unique task of each piece can be clearly understood and verified, and where the sequence of all executed instructions leaves no doubt. That is why functions are limited to 25 lines, and why `for`, `do...while`, or ternaries are forbidden.

- Look and Feel: while exchanging with your friends and workmates during normal peer-learning and peer-evaluations, you do not want to spend time decrypting code before discussing its logic.

  The Norm asks you to use a specific look and feel, with instructions for naming functions and variables, indentation, brace rules, tabs and spaces, and more. This allows you to quickly read others' code and focus directly on logic. The Norm is also a trademark of the 42 community.

- Long-term vision: making the effort to write understandable code is the best way to maintain it. Each time someone (including you) has to fix a bug or add a feature, they will not have to waste time trying to understand unclear code.

- References: some or all Norm rules may seem arbitrary, but they are based on established software engineering practices. You are encouraged to research topics such as short functions, meaningful naming, 80-column lines, parameter limits, and useful comments.

## III. The Norm

### III.1 Naming

- A structure's name must start by `s_`.
- A typedef's name must start by `t_`.
- A union's name must start by `u_`.
- An enum's name must start by `e_`.
- A global's name must start by `g_`.
- Identifiers (variables, function names, user-defined types) can only contain lowercase letters, digits, and `_` (snake_case). No capital letters are allowed.
- File and directory names can only contain lowercase letters, digits, and `_` (snake_case).
- Characters that are not part of standard ASCII are forbidden, except inside literal strings and chars.
- `(*)` All identifier names (functions, types, variables, etc.) should be explicit or mnemonic, readable in English, with words separated by underscores. This applies to macros, filenames, and directories as well.
- Using global variables that are not marked `const` or `static` is forbidden and considered a Norm error, unless the project explicitly allows them.
- The file must compile. A file that does not compile is not expected to pass the Norm.

### III.2 Formatting

- Each function must be at most 25 lines long, not counting the function's own braces.
- Each line must be at most 80 columns wide, comments included. Warning: a tabulation does not count as a single column, but as the number of spaces it represents.
- Functions must be separated by an empty line. Comments or preprocessor instructions can be inserted between functions. At least one empty line must exist.
- You must indent your code with 4-character tabulations. This is not the same as 4 spaces: real tabulations are required (ASCII char 9). Configure your editor accordingly.
- Blocks within braces must be indented. Braces are alone on their own line, except in declarations of `struct`, `enum`, and `union`.
- An empty line must be empty: no spaces or tabulations.
- A line can never end with spaces or tabulations.
- You can never have two consecutive empty lines. You can never have two consecutive spaces.
- Declarations must be at the beginning of a function.
- All variable names must be indented on the same column in their scope. Note: types are already indented by the containing block.
- The asterisks that go with pointers must be stuck to variable names.
- One single variable declaration per line.
- Declaration and initialization cannot be on the same line, except for global variables (when allowed), static variables, and constants.
- In a function, you must place an empty line between variable declarations and the rest of the function. No other empty lines are allowed in a function.
- Only one instruction or control structure per line is allowed (e.g. assignment in a control structure is forbidden, multiple assignments on the same line are forbidden, etc.).
- An instruction or control structure can be split into multiple lines when needed. The following lines must be indented compared to the first line, natural spaces are used to cut the line, and operators should be at the beginning of the new line (not the end of the previous one).
- Unless it is the end of a line, each comma or semicolon must be followed by a space.
- Each operator or operand must be separated by one (and only one) space.
- Each C keyword must be followed by a space, except type keywords (`int`, `char`, `float`, etc.) and `sizeof`.
- Control structures (`if`, `while`, etc.) must use braces, unless they contain a single instruction on a single line.

### III.3 Functions

- A function can take 4 named parameters at most.
- A function that does not take arguments must be explicitly prototyped with the word `void` as the argument.
- Parameters in function prototypes must be named.
- You cannot declare more than 5 variables per function.
- Return of a function has to be between parenthesis, unless the function returns nothing.
- Each function must have a single tabulation between its return type and its name.

### III.4 Typedef, struct, enum and union

- As with other C keywords, add a space between `struct` and the name when declaring a struct. Same for `enum` and `union`.
- When declaring a variable of type struct, apply usual indentation for the variable name. Same for `enum` and `union`.
- Inside braces of `struct`, `enum`, and `union`, regular indentation rules apply like any other blocks.
- As with other C keywords, add a space after `typedef`, and apply regular indentation for the new defined name.
- You must indent all structure names on the same column for their scope.
- You cannot declare a structure in a `.c` file.

### III.5 Headers - a.k.a include files

- `(*)` Allowed elements of a header file are: header inclusions (system or not), declarations, defines, prototypes, and macros.
- All includes must be at the beginning of the file.
- You cannot include a C file in a header file or another C file.
- Header files must be protected from double inclusions. If the file is `ft_foo.h`, its bystander macro is `FT_FOO_H`.
- `(*)` Inclusion of unused headers is forbidden.
- Header inclusion can be justified in the `.c` file and in the `.h` file itself using comments.

### III.6 The 42 header - a.k.a start a file with style

- Every `.c` and `.h` file must immediately begin with the standard 42 header: a multi-line comment with a special format including useful information. The standard header is available on cluster computers for various editors (emacs: `C-c C-h`, vim: `:Stdheader` or `F1`, etc.).
- `(*)` The 42 header must contain up-to-date information, including creator login and student email (`@student.campus`), creation date, and last update login/date. Each save should update this information automatically.

### III.7 Macros and Pre-processors

- `(*)` Preprocessor constants (`#define`) you create must be used only for literal and constant values.
- `(*)` All `#define` created to bypass the Norm and/or obfuscate code are forbidden.
- `(*)` You can use macros available in standard libraries only if they are allowed in the scope of the given project.
- Multiline macros are forbidden.
- Macro names must be all uppercase.
- You must indent preprocessor directives inside `#if`, `#ifdef`, or `#ifndef` blocks.
- Preprocessor instructions are forbidden outside of global scope.

### III.8 Forbidden stuff

- You are not allowed to use:
  - `for`
  - `do...while`
  - `switch`
  - `case`
  - `goto`
- Ternary operators such as `?`.
- VLAs (Variable Length Arrays).
- Implicit type in variable declarations.

### III.9 Comments

- Comments cannot be inside function bodies. Comments must be at the end of a line, or on their own line.
- `(*)` Your comments should be in English and useful.
- `(*)` A comment cannot justify the creation of a carryall or bad function.

### III.10 Files

- You cannot include a `.c` file in a `.c` file.
- You cannot have more than 5 function definitions in a `.c` file.

### III.11 Makefile

Makefiles are not checked by norminette and must be checked during evaluation by the student when asked by evaluation guidelines. Unless specific instructions are given, the following rules apply:

- The `$(NAME)`, `clean`, `fclean`, `re`, and `all` rules are mandatory. The `all` rule must be the default one and run when typing `make`.
- If the Makefile relinks when not necessary, the project is considered non-functional.
- In a multibinary project, in addition to the rules above, you must have a rule for each binary (e.g. `$(NAME_1)`, `$(NAME_2)`, ...). The `all` rule compiles all binaries using each binary rule.
- In a project that calls a function from a non-system library (e.g. `libft`) that exists along your source code, your Makefile must compile this library automatically.
- All source files needed to compile your project must be explicitly named in the Makefile (e.g. no `*.c`, no `*.o`, etc.).
