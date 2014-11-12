# Pedanticism

You left in the TODO paragraph at the top of your notebook! :P

# Real critique

## Syntax

The syntax seems like it is a bit overdefined. There isn't a whole lot
of flexibility, which might make using the language for anything you
haven't explicitly worked on difficult, because it seems like it
relies very heavily on building sentences out of highly specified
keywords. Is my understanding correct? 

## IR

The IR seems like it's designed to follow the syntax fairly rightly,
rather than being designed specifically to ease implementation in
scala. How do you intend to translate these things semantically
without a huge blowup in the number of code paths you have to worry
about (e.g. branching on hours vs days vs weeks)? It might be better
to only have one IR time unit that everything else is immediately
converted to, for example. Also, it seems like your IR specification
is partly a syntax specification rather than an actual IR (you don't
need to define what a number is in an IR, for example).

In terms of data structure, it seems like performance isn't too much
of an issue because it's unlikely a user will have more than a few
hundred TODOs coming up, and on n ~= 100 even a list is plenty
performant.
