# <?php function styleguide() {
    /* A style guide that will make you go ['hip', 'hip']. */
    
# Index
- [PSR Overview](#psr-overview) <a name="properties"></a>
- [Lines](#lines)
- [Indentation](#indentation)
- [Keywords](#keywords)
- [Namespace and Use Statements](#namespace-use)
- [Classes, properties and methods](#classes-properties-methods)
- [Extends and Implements](#extends-implements)
- [Traits](#traits)
- [Properties](#properties)
- [Methods](#methods)
- [Method and Function Arguments](#method-function-args)
- [Method and Function Calls](#method-function-calls)
- [Control Structures](#control-structures)
- [Absract, Static and Final](#abstract-final-static)
- [if, elseif, else](#if-elseif-else)
- [switch, case](#switch-case)
- [Operators](#operators)
- [Closures](#closures)
- [Anonymous Classes](#anonymous-classes)
- [Casts](#casts)
- [Comments](#comments)
- [Strings](#strings)
    
## Basic Coding Standards
When writing PHP, always use a routing framework and a templating language.

## [§](#psr-overview) <a name="psr-overview"></a>PSR-1 Overview
* Files must only use `<?php` tags. Ending tags should **always** be ommitted.
* Files must use only UTF-8 without BOM and use Unix LF line ending.
    * All PHP files must end with a single line, containing only a single newline (LF) character. This rule should not be overridden by any other rule in this document.
* Files should either declare symbols (classes, functions, constants, etc.) or cause side-effects (e.g. generate output, change .ini settings, etc.) but should not do both.
* Namespaces and classes must follow [PSR4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md)
* Class names must use PascalCase.
* Method names must use camelCase.
* Constants must always be declared in all upper case with underscore separators.

For examples of each of these please see [PSR1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md).

## [§](#lines) <a name="lines"></a>Lines
There is not a hard limit on line length.

The soft limit on line limit is 120 characters.

Lines should aim to be less than 80 characters.

There must not be trailing whitespace at the end of lines

Blank lines may be used to improve readability.

There must not be more than one statement per line.

## [§](#indentation) <a name="indentation"></a>Indentation
All code must use 4 space indentation no matter what. Tabs must not be used under any circumstances.

## [§](#keywords) <a name="keywords"></a>Keywords
PHP keywords must always be in lower case.

The PHP types and keywords `array`, `int`, `true`, `object`, `float`, `false`, `mixed`, `bool`, `null`, `numeric`, `string`, `void` and `resource` must be in lower case.

## [§](#namespace-use) <a name="namespace-use"></a>Namespace and use statements
When the opening `<?php` tag is on the first line of the file, it must be on its own line with no other statements unless it is a file containing markup outside of PHP opening and closing tags.

There must be one blank line after the `namespace` declaration.

All `use` declarations must go after the `namespace` declaration.

There must be one `use` keyword per declaration.

## [§](#classes-properties-methods) <a name="classes-properties-methods"></a>Classes, Properties and Methods
The term "class" refers to all classes, interfaces, and traits.

Starting braces if classes and methods must be on their own line directly after the body, they should not be followed by or preceded by a blank line.

Any closing brace must not be followed by any comment or statement on the same line, they should not be preceded by a blank line.

When instantiating a new class, parenthesis must not be present when there are no arguments passed to the constructor.

## [§](#extends-implements) <a name="extends-implements"></a>Extends and Implements

The `extends` and `implements` keywords must be declared on the same line as the class name.

Lists of `implements` and `extends` may be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list must be on the next line, and there must be only one interface per line.

## [§](#traits) <a name="traits"></a>Traits

The `use` keyword used inside classes to implement traits must be declared on the line directly after the opening brace.

Traits must be included one per line, and each inclusion must have its own use statement.

When the class has no methods or parameters, the class closing brace must be on the next line after the use statements, otherwise it must have a blank line after the `use` statements.

## [§](#properties) <a name="properties"></a>Properties

Visibility must be declared on all properties. The `var` keyboard must not ever be used.

Properties must be declared one per line. They must not be prefixed with a single underscore to indicate protected or private visibility.

## [§](#methods) <a name="methods"></a>Methods

Visibility must be declared on all methods.

Method names must be prefixed with a single underscore to indicate protected or private visibility. 

Method and function names must not be declared with a space after the method name.

The opening brace must go on its own line, and the closing brace must go on the next line following the body. There must be a space after the opening parenthesis, and there must not be a space before the closing parenthesis.

Do not declare useless overridden methods (ie: do not just declare a method which calls `parent::methodName()`)

Never declare inner functions.

## [§](#method-function-args) <a name="method-function-args"></a>Method and Function Arguments

In the argument list, there must not be a space before each comma, and there must be one space after each comma.

Method and function arguments with default values must go at the end of the argument list.

Method and function argument scalar type hints must be lowercase.

A return type is required whenever a single one can be defined.

In return type declarations, the colon must be both prefixed and followed by a single space.

Argument lists may be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list must be on the next line, and there must be only one argument per line.

When the argument list is split across multiple lines, the closing parenthesis and opening brace must be placed together on their own line with one space between them. The colon and declaration must be on the same line as the argument list closing parentheses. The declaration keyword (e.g. `string`) must be lowercase.

## [§](#method-function-calls) <a name="method-function-calls"></a>Method and Function Calls

When making a method or function call, there must not be a space between the method or function name and the opening parenthesis.

There must be a space after the opening parenthesis, and there must be a space before the closing parenthesis.

In the argument list, there must not be a space before each comma, and there must be one space after each comma.

Argument lists may be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list must be on the next line, and there must be only one argument per line. A single argument being split across multiple lines (as might be the case with an anonymous function or array) does not constitute splitting the argument list itself.

Never use call-time pass by reference.

Do not use deprecated methods.

Never call methods using the silence (`@`) operator. Never use the `eval` method.

Do not use `$this` in a static context.

## [§](#control-structures) <a name="control-structures"></a>Control Structures

The general style rules for control structures are as follows:

* There must be one space after the control structure keyword
* There must not be a space after the opening parenthesis
* There must not be a space before the closing parenthesis
* There must be one space between the closing parenthesis and the opening brace
* The structure body must be indented once
* The closing brace must be on the next line after the body

The body of each structure must be enclosed by braces. This standardizes how the structures look, and reduces the likelihood of introducing errors as new lines get added to the body.

Always use `while` loops rather than `for` loops where possible. Stay away from C-style  `for (;;) {}` loops and sway towards `while (true)` loops. Prefer `foreach` over `for` for arrays always.

## [§](#abstract-final-static) <a name="abstract-final-static"></a>abstract, final, and static

When present, the `abstract` and `final` declarations must follow the visibility declaration.

When present, the `static` declaration must come before the `abstract` and `final` modifiers but after the visibility declaration.


## [§](#if-elseif-else) <a name="if-elseif-else"></a>if, elseif, else

Please note the placement of parentheses, spaces, and braces; and that else and elseif are on the same line as the closing brace from the earlier body. The same can be applied to `do while` statements and `try`, `catch`, `finally` blocks.

    if ($expr) {
        // body
    } elseif ($expr2) {
        // body
    } else {
        // body
    }

The keyword `elseif` should be used instead of else if so that all control keywords look like single words.

`if` statements must never be empty.

## [§](#switch-case) <a name="switch-case"></a>switch, case

The case statement must be indented once from switch, and the break keyword (or other terminating keyword) must be indented at the same level as the case body. 

## [§](#operators) <a name="operators"></a>Operators
All binary and ternary (but not unary) operators must be preceded and followed by at least one space. This includes all arithmetic, comparison, assignment, bitwise, logical (excluding `!` which is unary), string concatenation, and type operators.

## [§](#closures) <a name="closures"></a>Closures
Closures must be declared with a space after the `function` keyword, and a space before and after the `use` keyword.

The opening brace must go on the same line, and the closing brace must go on the next line following the body.

There must be a space after the opening parenthesis of the argument list or variable list, and there must not be a space before the closing parenthesis of the argument list or variable list.

In the argument list and variable list, there must not be a space before each comma, and there must be one space after each comma.

Closure arguments with default values must go at the end of the argument list.

Argument lists and variable lists may be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list must be on the next line, and there must be only one argument or variable per line.

When the ending list (whether or arguments or variables) is split across multiple lines, the closing parenthesis and opening brace must be placed together on their own line with one space between them.

## [§](#anonymous-classes) <a name="anonymous-classes"></a>Anonymous Classes

Anonymous Classes must follow the same guidelines and principles as [closures](#closures) in the above section.

The opening parenthesis may be on the same line as the class keyword so long as the list of implements interfaces does not wrap. If the list of interfaces wraps, the parenthesis must be placed on the line immediately following the last interface.

## [§](#casts) <a name="casts"></a>Casts

Casts must always be followed by a space. There should not be a space inside the casts parenthesis.

## [§](#comments) <a name="comments"></a>Comments

All classes should have a PHP docblock. All classes should declare an `@author` property in the form of `Firstname Lastname <email@address.com>`.

All methods and functions should have a PHP docblock. Each parameter should have a `@param` tag containing: the data type, then the parameter's name, followed by a description. These docblocks should also have `@return` tag.

`@return` tags should contain the data type, then a description of the data returned by the method or function. Use `void` if nothing is returned.

All docblocks should always have a short description of the function and purpose of the method, it should also have a longer description if needed.

No code should be commented out in the master branches.

## [§](#strings) <a name="strings"></a>Strings

All strings should use single quotes if they do not use string interpolation. In the event of string interpolation then double quotes are permitted. If you require more advanced data in the string than just a simple variable, consider using the `sprintf` C-style method.

#}