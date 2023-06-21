# SyntaxAlchemist
The vision of this project is to create a meta-tool using which it becomes trivial to build toolsets that work on tiny domain-specific or tiny abstract languages or data-formats. On one side, it is concerned with the human-facing side of operation: providing an intentional editing experience. The other side is the incremental transformation between different representations, as there are always different tradeoffs for the best representation of choice depending on the use, be it CPU-friendly or compressed or humanized formats.
For the human-facing end, it generates structured editing tools either by an a-priori language design or by ad-hoc reversing a given data pice into its grammar.
Further, incremental live-transformations a.k.a projections can be utilized to add the desired syntax flavours ontop of the abstract syntax for disambiguation and readability.
We aim to build a foundation for user interfaces with a keyboard-driven approach to edit code in a tree-structured, language-aware fashion, from which data-views can be accessed and transformed in multiple different representations, allowing to decouple the user-facing data formats from internal ones with the help of *ladder typing* by automatic application of homomorphic transformations.

## Demo
The current research application is a shell-like REPL that
* makes use of syntax-based editing in order to input the command to be executed, implemented with [Nested-library](https://github.com/michaelsippel/nested)
* and typed pipelines, where *ladder-typing* introduces a structural subtyping relation.

[![asciicast](https://asciinema.org/a/580755.svg)](https://asciinema.org/a/580755)

## Key Concepts

### Nested Structural Editing
#### Keyboard-based Interaction (not text-based!)
#### Tree Cursor
#### Projectional Pipes
Human-readable views of objects are created by structured projections from lower-level representations.
This is done by typed pipelines that can on the fly transform various conceptual structures,
through a notification-request based mechanism where changes are propagated in real-time.

-> solve 'leaning toothpick' syndrome with color coding
-> formatting
-> LSP
-> diff piping

### Ladder Typing
#### Polyiconic Objects
#### Semantic Equivalence

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
