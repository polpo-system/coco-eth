# Coco/R of ETH Oberon, for polpo

Coco/R is the compiler generator of H. Moessenboeck (ETH Zurich): it reads an attributed
grammar (`NAME.ATG`) and writes the scanner (`NAMES.Mod`) and the parser (`NAMEP.Mod`) of
the language. This is version 2.2 as it came with Native Oberon 2.3.6, unchanged: the
sources, the frames, its own grammar and the tool text `Coco.Tool`.

polpo compiles it as it is, on all its architectures (x86, ARM, ARMv7, RISC-V, MIPS).

## What is here

    Coco.Tool       the tool text: the commands and a short manual
    CR.ATG          the grammar of Coco/R itself
    Parser.FRM      the frame of the generated parser
    Scanner.FRM     the frame of the generated scanner
    src/Sets.Mod    sets of symbols
    src/CRS.Mod     the scanner of Coco/R (generated from CR.ATG, then edited by ETH)
    src/CRP.Mod     the parser of Coco/R (likewise)
    src/CRT.Mod     the symbol table and the grammar tests
    src/CRA.Mod     the scanner generator
    src/CRX.Mod     the parser generator
    src/Coco.Mod    the command Coco.Compile

## Installing

With portia, the package manager of polpo: `portia.Install coco-eth`. The frames go to
`share/` and `Coco.Tool` to `tools/`, where polpo finds them by name from any directory;
`CR.ATG` and the sources are in `src/pkg/coco-eth/`.

`coco-eth` conflicts with `coco`, the Coco/R 2012.01 of A. V. Shiryaev
(https://github.com/polpo-system/polpo-coco): both have the modules `Sets`, `CRS` ...
`Coco`. Installing one replaces the other.

## Using it

It is a desktop command (`loksh System.Init`): open `Coco.Tool`, then

    Coco.Compile name.ATG           a grammar file
    Coco.Compile name.ATG \X        with a cross reference list of the symbols
    Coco.Compile name.ATG \S        with the start symbols and the followers
    Coco.Compile *  (the marked viewer), ^ or @ (the selection)

The messages go to the log viewer (System.Log). A `Parser.FRM` or `Scanner.FRM` in the
current directory is used instead of the installed one.

## Compared with coco (2012.01)

The later version adds `IF(...)` resolvers for LL(1) conflicts, literals that are not
tokens, better conflict messages, a generated driver module, and a console front end
(`coco.Compile`); see the README of polpo-coco. This one is the reference: the Coco/R of
ETH Oberon as it was.

## License

The ETH Oberon license: see `LICENSE`.
