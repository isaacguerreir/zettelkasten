# Genetic Circuits Design by Constrains

While Benchling and Snapgene are the most used platforms to design genetic circuits, 
they all have the same akward feeling. Genetic design is hard. The feeling of working 
at bit-level is almost certain. That's exactly because you're. Base pairs are indistri-
guishible from anything. Annotations are a way we invented to discern between diffe-
rent sequences, to associate sequence to function.

If we could design sequences by defining a function or a constrain and let software read 
our requirements and 'compile' a base pair sequence? Well, let's write code to make this
and see if it feels more intuitive and easy to use than Benchling and Snapgene.

What are the software requirements?

- Give a list of constrains compile a DNA sequence

{
  constrains: [
    {
      contrain: "Random DNA"
      args: [
        "20bp",
        "GC>50",
        "GC<40"
      ]
    },
    {
      constrain: "Promoter Overhang - Golden Gate"
    },
    {
      contrain: "Random DNA"
      args: [
        "5bp",
        "GC>50",
        "GC<40"
      ]
    },
    {
      contrain: "BsaI Site"
    },
    {
      contrain: "Random DNA"
      args: [
        "10bp",
        "GC>50",
        "GC<40"
      ]
    },
  ],
  globalConstrain: [
    {
      constrain: "Remove repetitions",
      args: [
        ">12bp"
      ]
    }
  ]
}

- Import sequence
library.importPackage(GoldenGate)

## Lets deep dive around some possible entities

Library - Where all the collections, parts, constraint solver are available
Compiler - Function responsible for solve constrains and sequence assembly in optimal ways
Constrain - A constrain is a sequence that have one or more requirements

Input and outputs should be a JSON Document, because is web-compatible format and easy 
to understand.


