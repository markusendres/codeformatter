# CodeFormatter

[![Build status](http://dotnet-ci.cloudapp.net/job/dotnet_codeformatter/badge/icon)](http://dotnet-ci.cloudapp.net/job/dotnet_codeformatter/)

CodeFormatter is a tool that uses Roslyn to automatically rewrite the source to
follow our coding styles, which are documented below.

## Prerequisites

In order to build or run this tool you will need to have Microsoft Build Tools
2015 Preview installed.  This comes as a part of Visual Studio 2015 Preview or
can be installed separately from [here][vs-2015-download].

[vs-2015-download]: http://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs

## Usage

In order get the usage, simply invoke the tool with no arguments:

```
$ .\CodeFormatter.exe
CodeFormatter <project or solution> [<rule types>] [/file:<filename>] [/nocopyright] [/c:<config1,config2> [/copyright:file]
    <rule types> - Rule types to use in addition to the default ones.
                   Use ConvertTests to convert MSTest tests to xUnit.
    <filename>   - Only apply changes to files with specified name.
    <configs>    - Additional preprocessor configurations the formatter
                   should run under.
    <copyright>  - Specifies file containing copyright header.
```

## C# Coding Style

The general rule we follow is "use Visual Studio defaults".

We use Allman style braces, where each brace begins on a new line. A single line statement block can go without braces but the block must be properly indented on its own line and it must not be nested in other statement blocks that use braces (See issue 381 for examples).

We use four spaces of indentation (no tabs).

We use _camelCase private members and use readonly where possible. Prefix instance fields with _, static fields with s_ and thread static fields with t_.

We avoid this. unless absolutely necessary.

We always specify the visibility, even if it's the default (i.e. private string _foo not string _foo).

Namespace imports should be specified at the top of the file, outside of namespace declarations and should be sorted alphabetically, with `System. namespaces at the top and blank lines between different top level groups.

Avoid more than one empty line at any time. For example, do not have two blank lines between members of a type.

Avoid spurious free spaces. For example avoid if (someVar == 0)..., where the dots mark the spurious free spaces. Consider enabling "View White Space (Ctrl+E, S)" if using Visual Studio, to aid detection.

If a file happens to differ in style from these guidelines (e.g. private members are named m_member rather than _member), the existing style in that file takes precedence.

We only use var when it's obvious what the variable type is (i.e. var stream = new FileStream(...) not var stream = OpenStandardInput()).

We use language keywords instead of BCL types (i.e. int, string, float instead of Int32, String, Single, etc) for both type references as well as method calls (i.e. int.Parse instead of Int32.Parse). See issue 391 for examples.

We use PascalCasing to name all our constant local variables and fields. The only exception is for interop code where the constant value should exactly match the name and value of the code you are calling via interop.


## Contributing

We follow the same contribution process that 
[corefx is using][corefx-contributing].

[corefx-contributing]: https://github.com/dotnet/corefx/wiki/Contributing
