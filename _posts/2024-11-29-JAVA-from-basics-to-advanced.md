---
title: "JAVA: From Basics to Advanced"
date: 2024-11-29 20:33:00 +0530
categories: [Java]
tags: [java, jvm, oop, notes]
description: "JVM internals, classloading, memory areas, and core Java concepts distilled into structured study notes."
image: /assets/img/posts/java-from-basics-to-advanced.svg
---

## 1. JDK TOOLS

- `javac` = converts .java source files into .class bytecode.
- `java` = executes a program.
- `jar` = java archive (packaging files together).
- `javadoc` = java documentation.

## 2. JVM ARCHITECTURE

#### Overview:
- `ClassLoader + Memory Area + Execution Engine`

1.  Compilation:
- .class file is created which consists of bytecode

2. Byte Code:
- Machine-level instructions executed by JVM
- JVM converts bytecode into target machine/native code

3. Execution:
- java tool is used to execute the .class file
- Loads .class file from classpath
- Invokes JVM to execute the program

## 3. CLASSLOADER SUBSYSTEM
- Loads and initializes classes

#### Loading:
- Loads class files into JVM Method Area
- ClassLoaders:

1. `Bootstrap_ClassLoader:`
- Loads core Java classes
- path: "jre/lib (rt.jar)"

2. `Extension_ClassLoader:`
- Loads extended libraries
- path: "jre/lib/ext"

3. `Application_ClassLoader:`
- Loads classes from application classpath

#### Linking:
- Links loaded classes
- `steps:`
1. Verification: Ensures bytecode is valid and not tampered
2. Preparation: Allocates memory for static variables with default values
3. Resolution: Replaces symbolic references with direct references

#### Initialization:
- Assigns actual values to static variables
- Executes static blocks

## 4. MEMORY AREAS:
- JVM has 5 memory areas

#### Method_Area:
- Created during JVM startup
- Shared across threads
- Stores class metadata and method data
- Stores constant pool

#### Heap_Area:
- Created during JVM startup
- Shared across threads
- Stores all objects (created using new)
- Contains String Pool
- Class metadata stored in java.lang.Class objects

#### Stack_Area:
- Each thread has its own stack
- Created when thread is created

###### Stack_Frame:
- Created on method call
- Destroyed after method execution, contains:
1. Local_Variable_Array
2. Operand_Stack
3.  Frame_Data

#### Native_Method_Stack:
- Separate stack per thread
- Used for native method execution
- Creates stack frame for native calls

#### PC_Register:
- Each thread has its own PC register
- Stores address of next instruction
- Auto-increment after instruction execution

## 5. EXECUTION ENGINE:
- Core component that executes bytecode

#### Interpreter:
- Executes bytecode line by line
- Each method is interpreted at least once
- Slower for repeated calls

#### JIT_Compiler:
- Just-In-Time Compiler
- Improves performance
- Compiles frequently used methods into native code
- Caches compiled code for reuse

#### Profiler:
- Tracks resource usage (memory, threads)
- Identifies hotspots
- Counts method execution frequency
- Triggers JIT when threshold is exceeded

#### Garbage_Collector:
- Frees memory of unreferenced objects
- Prevents memory leaks

#### JNI:
- Java Native Interface
- Acts as bridge between Java and native code (C/C++)

## 6. PROGRAM ENTRY POINT

Main_Method:
  Syntax_Variations: {}

  Modifier_Order:
    - public_static
    - static_public

  Case_Sensitivity:
    valid: "main"
    invalid: "Main"

  Command_Line_Arguments: {}

  Compilation_Execution:
    - javac
    - "java -cp"

## 7. DATA TYPES & MEMORY

Data_Types:
  Primitive:
    Boolean: {}
    Char: {}

    Integral:
      - byte
      - short
      - int
      - long

    Floating:
      - float
      - double

  Reference:
    - class
    - interface
    - enum
    - array

  Type_Promotion_Rules:
    - "byte/short → int"
    - "int + long → long"
    - "float + long → float"
    - "double dominates all"

## 8. LITERALS

Literals:
  Integral: {}
  Floating_Point: {}

  Char:
    Escape_Sequences:
      - \n
      - \r
      - \t
      - \b
      - \'
      - '\"'
      - \\
      - \0

  String: {}
  Boolean: {}
  Null: {}

## 9. WRAPPER CLASSES

Wrapper_Classes:
  Boolean: {}
  Character: {}

  Number:
    - Byte
    - Short
    - Integer
    - Long
    - Float
    - Double

  Boxing: {}
  Unboxing: {}

## 10. CORE OOP CONCEPTS

OOP:
  Class_and_Object:
    - State
    - Behavior
    - Identity
    - Reference_Variables
    - this_keyword

  Constructors:
    Types:
      - Default
      - Parameterized

    Constructor_Chaining:
      this: {}
      super: {}

    Advanced_Object_Creation:
      - Reflection
      - Deserialization
      - clone
      - Unsafe_API

  Methods:
    - Overloading
    - Overriding

  Inheritance:
    - Single
    - Multilevel
    - Hierarchical
    - Multiple_via_Interface
    - Hybrid

  Polymorphism:
    - Compile_Time
    - Runtime
    - Upcasting
    - Downcasting

  Encapsulation: {}

  Abstraction:
    Abstract_Classes: {}
    Interfaces: {}

## 11. RELATIONSHIPS

Relationships:
  Association:
    Aggregation: {}
    Composition: {}

## 12. ARRAYS

Arrays:
  - One_Dimensional
  - Two_Dimensional
  - Ragged_Array
  - Primitive_Array
  - Reference_Array

## 13. KEYWORDS

Keywords:
  final:
    - Variables
    - Methods
    - Class

  static:
    - Variables
    - Methods
    - Block
    - Import

## 14. OBJECT CLASS METHODS

Object_Class:
  - equals
  - hashCode
  - toString
  - getClass
  - clone
  - finalize
  - wait
  - wait_with_timeout
  - notify
  - notifyAll

## 15. ABSTRACTION & INTERFACES

Abstract_and_Interfaces:
  Abstract_Class: {}
  Abstract_Methods: {}

  Interfaces:
    - Default_Methods
    - Static_Methods
    - Multiple_Inheritance

  Marker_Interfaces:
    - Serializable
    - Cloneable

  Fragile_Base_Class_Problem: {}

## 16. CLONING

Cloneable:
  - Shallow_Copy
  - Deep_Copy

## 17. ADVANCED TOPICS

Advanced:
  JVM:
    - JVM_Internals
    - Class_Loading_Mechanism

  Memory:
    - Garbage_Collection_Strategies
    - Memory_Management

  Reflection_and_IO:
    - Reflection_API
    - Serialization_Deserialization

  Concurrency:
    - Multithreading_Basics

  Performance:
    - Performance_Optimization

{% include comments.html %}
