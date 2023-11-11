# SyntaxAlchemist
The vision of `syntaxAlchemist` is to create a meta-tool using which it
becomes trivial to build toolsets that work on tiny
domain-specific/abstract languages/data-formats.

At high level, the main concern is to provide an intentional editing
experience where any kinds of data and code are presented to the user
in a meaningful, deeply structured way. Based on the users preferences
and language, any user-facing data is encoded accordingly and
therefore quickly readable and easy to manipulate.  Navigation and
editing is performed directly at AST-level (see *Tree-Navigation* /
*Tree-Cursor*) and projected into a view. Now in order now map these
user-facing representations back into formats that are easy to
process, automatic transformation between different representations is
required.

Most likely, different languages/formats are used for executing a
program than for inputting it, where via compilation the former can be
derived from the latter. Similarly, there might result different
representations from balacing out tradeoffs of storage- or
compute-friendly formats in addition to the humanized format.

To help accelerate the development process, immediate feedback from
continuous code-analyses is benefical during editing.  Therefore we
require a continuous transformation of the user-facing representation
(some specifically layouted concrete syntax tree) into some interal
representation, which is a more direct representation of the abstract
syntax and therefore easier to handle in analysis.
Conversely, incremental live-transformations a.k.a
projections are also utilized to add the desired syntax flavours ontop
of the abstract syntax for disambiguation and readability.

With the help of `syntaxAlchemist`, the task of composing new DSLs and
their according intellligent tooling could amount to specifying either
an a-priori language through a grammar-DSL, or by ad-hoc reversing a
given datum into its grammar by piece-wise decomposition,
interpretation and consequently transformation into a more abstract
view.

## Repository Structure
In its entirety, `syntaxAlchemist` is a complex software suite,
which is currently partitioned into the following sub-projects:

* [lib-laddertypes](https://github.com/michaelsippel/lib-laddertypes)
  — Rust Library for handling *Ladder-Types*, including (un-)parsing &
  rewriting, in particular (de-)currying, (de-)normalization and
  unification of type terms.
* [ltsh](https://github.com/michaelsippel/ltsh) — Utility program for
  type-checking shell-scripts based on *Ladder-Typing*.
* [lib-r3vi](https://github.com/michaelsippel/lib-r3vi) — Rust Runtime
  for functional composition of *reactive* view-projections with
  fine-grained *incremental* updates.  This library provides the
  primitives for creating complex views of data through functional
  pipelines of projections, which is useful for projecting UI-elements
  and editors from natively packed data.
* [lib-nested](https://github.com/michaelsippel/lib-nested) —
  Primitives for building syntax-based, keyboard-driven editors. Based
  on `lib-r3vi`, this library provides implementations of basic
  editors like `Char`, `PositionalInteger`, `List`, but also
  `TypeTerm`, which in turn can be composed into complex
  editors for algebraic types.
* [editorplayground](editorplayground) — Testbed for development of
  `lib-nested` & `lib-r3vi`.
* [shell](https://github.com/michaelsippel/shell) — Experimental Shell
  with synax-based command-input & type-system.  This application
  creates an editor for inputting the shell-command through
  `lib-nested`, then performs the type-check using
  `lib-laddertypes`. In the following demo, this type-analysis can be
  seen in action.

## Demo
[![asciicast](https://asciinema.org/a/580755.svg)](https://asciinema.org/a/580755)

## Key Concepts

### Ladder Typing
TODO

### Nested Structural Editing
One goal of `syntaxAlchemist` is to provide a dynamic, fully
structured method of editing data and code, based on the abstract
syntax which in turn is specified through typing of the data.

#### Keyboard-based Interaction (not text-based!)
The classical unix shells can be considered *text-based*, because they
wait for the program to be fully written out before starting the
parsing process. When editing this source program, it is treated as
plain text, without regard to its syntactical structure.

#### Tree Cursor
In *text*-editing the cursor is simply an index into a two dimensional
array, which is derived from a one dimensional one by separating on
newline characters.

With our syntax-based approach, the cursor points to a specific node
in the *syntax-tree* and is therefore also called a *tree-cursor*. It is
representant by a `Vec<usize>`, giving essentially a path that spans
the syntax-tree top down.  Consequently, navigation is based on this syntax-tree aswell, where we make use of an extended control pad to move around sibling-/parent-/cousin- nodes.

#### Projectional Pipes
Human-readable views of objects are created by structured projections
from lower-level representations.  This is done by typed pipelines
that can transform various conceptual structures on the fly through a
notification-request based mechanism where changes are propagated in
real-time.

## Kindred Spirits
...mostly so called "Language Workbenches", "Projectional Editors" and "Structured Editors"

- [colorForth](https://colorforth.github.io/cf.htm)
- [lambdu](https://github.com/lamdu/lamdu)
- [ProjecturEd](https://github.com/projectured/projectured)
- [Sapling](https://github.com/kneasle/sapling)
- [Nushell](https://www.nushell.sh/)
- [ACME (by Rob Pike)](http://acme.cat-v.org/)
- [Intellij MPS](https://www.jetbrains.com/mps/)
- [Paredit mode (emacs)](https://www.emacswiki.org/emacs/ParEdit)
- [Emily (by Wilfred J. Hansen)](https://www.cs.cmu.edu/~wjh/Emily.html)
- [Andrew](https://www.cs.cmu.edu/afs/cs.cmu.edu/Web/People/AUIS/)
- [sketch-n-sketch](https://ravichugh.github.io/sketch-n-sketch/index.html)
- [Dion Systems](https://dion.systems/)
- [Roc](https://www.roc-lang.org/)
- [Cirru](https://cirru.org/)
