<div class="cover-page" align=center STYLE="page-break-after: always;">

<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

<div class="cover-title">UCB CS61A</div>

<div class="cover-subtitle">Structure and Interpretation of Computer Programs</div>

</div>

<div class="toc-page" STYLE="page-break-after: always;">

# CONTENTS {ignore=true}

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=true} -->

<!-- code_chunk_output -->

1. [Functions](#functions)
    1. [Call Expressions](#call-expressions)
    2. [Names, Assignment, and User-Defined Functions](#names-assignment-and-user-defined-functions)
    3. [Environment Diagrams](#environment-diagrams)
    4. [Defining Functions](#defining-functions)
    5. [Print and None](#print-and-none)
        1. [None](#none)
    6. [Pure Functions & None-Pure Functions](#pure-functions--none-pure-functions)
2. [Control](#control)
    1. [Multiple Environments](#multiple-environments)
    2. [Miscellaneous Python Features](#miscellaneous-python-features)
        1. [Division](#division)
        2. [Return Multiple Values from a Function](#return-multiple-values-from-a-function)
        3. [Interactive Mode](#interactive-mode)
        4. [Doc Test](#doc-test)
        5. [Default Values](#default-values)
    3. [Conditional Statements](#conditional-statements)
        1. [Boolean Context](#boolean-context)
    4. [Iteration](#iteration)
        1. [While Statement](#while-statement)
3. [Higher-Order Functions](#higher-order-functions)
    1. [Control Expressions](#control-expressions)
        1. [Logical Operators](#logical-operators)
        2. [Assertion](#assertion)
    2. [Higher-Order Functions](#higher-order-functions-1)
    3. [Functions as Return Values](#functions-as-return-values)
4. [Environments](#environments)
    1. [Environments for Higher-Order Functions](#environments-for-higher-order-functions)
    2. [Environments for Nested-Definitions](#environments-for-nested-definitions)
    3. [Local Names](#local-names)
    4. [Function Composition](#function-composition)
    5. [Lambda Expressions](#lambda-expressions)
    6. [Function Currying](#function-currying)
5. [Functional Abstraction](#functional-abstraction)
    1. [Lambda Function Environments](#lambda-function-environments)
    2. [Return](#return)
    3. [Abstraction](#abstraction)
    4. [Errors and Tracebacks](#errors-and-tracebacks)
6. [Function Examples](#function-examples)
    1. [Decorators](#decorators)
    2. [Project - Hog: Arbitrary Positional Arguments](#project---hog-arbitrary-positional-arguments)
7. [Recursion](#recursion)
    1. [Self-Reference](#self-reference)
    2. [Recursive Functions](#recursive-functions)
    3. [Mutual Recursion](#mutual-recursion)
        1. [The Luhn Algorithm](#the-luhn-algorithm)
8. [Tree Recursion](#tree-recursion)
    1. [Example: Inverse Cascade](#example-inverse-cascade)
    2. [Tree Recursion](#tree-recursion-1)
    3. [Example: Counting Partitions](#example-counting-partitions)
    4. [HW03: Anonymous Factorial](#hw03-anonymous-factorial)
        1. [Conditional Expressions](#conditional-expressions)
        2. [Anonymous Factorial](#anonymous-factorial)
9. [Sequences](#sequences)
    1. [Lists](#lists)
    2. [Containers](#containers)
    3. [For Statements](#for-statements)
        1. [Sequence Iteration](#sequence-iteration)
        2. [For Statement Execution Procedure](#for-statement-execution-procedure)
        3. [Sequence Unpacking in For Statement](#sequence-unpacking-in-for-statement)
    4. [Ranges](#ranges)
    5. [List Comprehensions](#list-comprehensions)
    6. [Lists, Slices, & Recursion](#lists-slices--recursion)
10. [Containers](#containers-1)
    1. [Box-and-Pointer Notation](#box-and-pointer-notation)
        1. [The Closure Property of Data Types](#the-closure-property-of-data-types)
        2. [Box-and-Pointer Notation in Environment Diagrams](#box-and-pointer-notation-in-environment-diagrams)
    2. [Slicing](#slicing)
    3. [Processing Container Values](#processing-container-values)
        1. [Sequence Aggregation](#sequence-aggregation)
            1. [Sum](#sum)
            2. [Max](#max)
            3. [All](#all)
    4. [Strings](#strings)
        1. [String literals](#string-literals)
        2. [String are Sequences](#string-are-sequences)
    5. [Dictionaries](#dictionaries)
        1. [Dictionary Comprehensions](#dictionary-comprehensions)
            1. [Example: Indexing](#example-indexing)
11. [Data Abstraction](#data-abstraction)
    1. [Example: Rational Numbers](#example-rational-numbers)
    2. [Representing Rational Numbers](#representing-rational-numbers)
    3. [Abstraction Barrier](#abstraction-barrier)
        1. [Violating Abstraction Barriers](#violating-abstraction-barriers)
    4. [Data Representations](#data-representations)
12. [Tree](#tree)
    1. [Implementing the Tree Abstraction](#implementing-the-tree-abstraction)
    2. [Tree Processing](#tree-processing)
        1. [Count Leaves](#count-leaves)
        2. [Printing Trees](#printing-trees)
        3. [Summing Paths](#summing-paths)
        4. [Counting Path](#counting-path)
13. [Mutability](#mutability)
    1. [Objects](#objects)
    2. [Example: Strings](#example-strings)
        1. [Representing Strings: the ASCII Standard](#representing-strings-the-ascii-standard)
        2. [Representing Strings: the Unicode Standard](#representing-strings-the-unicode-standard)
    3. [Mutation Operations](#mutation-operations)
    4. [Tuples](#tuples)
    5. [Mutation](#mutation)
        1. [Identity Operators](#identity-operators)
        2. [Mutable Default Arguments](#mutable-default-arguments)
    6. [Mutable Functions](#mutable-functions)
14. [Iterators](#iterators)
    1. [For Statements](#for-statements-1)
    2. [Built-In Iterator Functions](#built-in-iterator-functions)
    3. [Zip](#zip)
15. [Generators](#generators)
    1. [Generator Function](#generator-function)
    2. [Generators &  Iterators](#generators---iterators)
    3. [Example: Partitions](#example-partitions)
16. [Objects](#objects-1)
    1. [Class Statements: the Account Class](#class-statements-the-account-class)
    2. [Creating Instances](#creating-instances)
    3. [Methods](#methods)
        1. [Invoking Methods](#invoking-methods)
17. [Attributes](#attributes)
    1. [Attribute Lookup](#attribute-lookup)
    2. [Class Attributes](#class-attributes)
    3. [Bound Methods](#bound-methods)
    4. [Attribute Assignment](#attribute-assignment)
18. [Inheritance](#inheritance)
    1. [Inheritance example](#inheritance-example)
    2. [Looking up Attribute Names on Classes](#looking-up-attribute-names-on-classes)
        1. [A Complicated Example](#a-complicated-example)
    3. [Multiple Inheritance](#multiple-inheritance)
19. [Representation](#representation)
    1. [String Representations](#string-representations)
    2. [String Interpolation](#string-interpolation)
    3. [Polymorphic Functions](#polymorphic-functions)
        1. [Interface](#interface)
    4. [Special Method Names](#special-method-names)
20. [Efficiency](#efficiency)
    1. [Measuring Efficiency](#measuring-efficiency)
    2. [Memoization](#memoization)
21. [Scheme](#scheme)
    1. [Scheme Fundamentals](#scheme-fundamentals)
    2. [Special Forms](#special-forms)
    3. [Lambda Expressions](#lambda-expressions-1)
    4. [Example: Sierpinski's Triangle](#example-sierpinskis-triangle)
22. [Scheme Lists](#scheme-lists)
    1. [Lists](#lists-1)
    2. [Symbolic Programming](#symbolic-programming)
    3. [Built-in List Processing Procedures](#built-in-list-processing-procedures)
    4. [Example: Even Subsets](#example-even-subsets)
    5. [Discussion Question: Even Subsets Using Filter](#discussion-question-even-subsets-using-filter)
23. [Calculator](#calculator)
    1. [Exceptions](#exceptions)
        1. [Raise Statements](#raise-statements)
        2. [Try Statements](#try-statements)
    2. [Example: Reduce](#example-reduce)
    3. [Parsing](#parsing)
24. [SQL](#sql)
    1. [Databases](#databases)
        1. [Declarative Programming](#declarative-programming)
    2. [Structured Query Language](#structured-query-language)
        1. [Selecting Value Literals](#selecting-value-literals)
        2. [Naming Tables](#naming-tables)
    3. [Projecting Tables](#projecting-tables)
        1. [Select Statements Project Existing Tables](#select-statements-project-existing-tables)
    4. [Arithmetic](#arithmetic)
        1. [Arithmetic in Select Expressions](#arithmetic-in-select-expressions)
25. [Tables](#tables)
    1. [Joining Tables](#joining-tables)
        1. [Joining Two Tables](#joining-two-tables)
        2. [Implicit & Explicit Join Syntax](#implicit--explicit-join-syntax)
    2. [Aliases and Dot Expressions](#aliases-and-dot-expressions)
        1. [Joining a Table with Itself](#joining-a-table-with-itself)
        2. [Joining Multiple Tables](#joining-multiple-tables)
    3. [Numerical Expressions](#numerical-expressions)
    4. [String Expressions](#string-expressions)
26. [Aggregation](#aggregation)
    1. [Aggregate Functions](#aggregate-functions)
        1. [Mix Aggregate Functions and Single Values](#mix-aggregate-functions-and-single-values)
    2. [Groups](#groups)
        1. [Grouping Rows](#grouping-rows)
27. [Databases](#databases-1)
    1. [Create Table and Drop Table](#create-table-and-drop-table)
        1. [Create Table](#create-table)
    2. [Drop Table](#drop-table)
    3. [Modifying Tables](#modifying-tables)
        1. [Insert](#insert)
        2. [Update](#update)
        3. [Delete](#delete)

<!-- /code_chunk_output -->

</div>

<div class="main-content" STYLE="page-break-after: always;">

@import "01 Functions.md"
@import "02 Control.md"
@import "03 Higher-Order Functions.md"
@import "04 Environments.md"
@import "05 Functional Abstraction.md"
@import "06 Function Examples.md"
@import "07 Recursion.md"
@import "08 Tree Recursion.md"
@import "09 Sequences.md"
@import "10 Containers.md"
@import "11 Data Abstraction.md"
@import "12 Trees.md"
@import "13 Mutability.md"
@import "14 Iterators.md"
@import "15 Generators.md"
@import "16 Objects.md"
@import "17 Attributes.md"
@import "18 Inheritance.md"
@import "19 Representation.md"
@import "20 Efficiency.md"
@import "21 Scheme.md"
@import "22 Scheme Lists.md"
@import "23 Calculator.md"
@import "24 SQL.md"
@import "25 Tables.md"
@import "26 Aggregation.md"
@import "27 Databases.md"

</div>