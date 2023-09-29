# csharp-tree-sitter
==================

# Introduction
This module provides C# bindings to the [tree-sitter](https://github.com/tree-sitter/tree-sitter) parsing library, which can enable c# developers be able to invoke the tree-sitter libraries through P/Invoke from their c# code.

# Build and Test
TODO: Describe and show how to build your code and run the tests.

# Contribute
TODO: Explain how other users and developers can contribute to make your code better.

If you want to learn more about creating good readme files then refer the following [guidelines](https://docs.microsoft.com/en-us/azure/devops/repos/git/create-a-readme?view=azure-devops). You can also seek inspiration from the below readme files:
- [ASP.NET Core](https://github.com/aspnet/Home)
- [Visual Studio Code](https://github.com/Microsoft/vscode)


## Cloning

This repo includes the needed tree-sitter repos as submodules.  Remember to use the `--recursive` option with git clone.

```cmd
git clone https://github.com/DennySun2020/csharp-tree-sitter.git --recursive
```

# Usage

To run c# building test, you need to build the tree-sitter parsers and the test code itself.

To build the tree-sitter parsers:

```cmd
cd tree-sitter`
nmake
```

To build the test:

```cmd
dotnet build src\csharp-tree-sitter.csproj
```

# Demo

A good demo is the following:

```cmd
csharp-tree-sitter.exe -files [your test cpp files]
```