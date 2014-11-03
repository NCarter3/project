# Project description and plan

## Motivation

Google calendar allows for easy due date processing
for todo lists. It does not handle contextual
computations, projects, relational due dates, recurring
events
or due times. [Todo.txt](todotxt.com)
has a rich interface for 
calculating contextual information for todo
items. It also is powerful for setting task 
priorities and grouping tasks by project.
However, it does not have the ability
to express anything related to due dates and
compute on them. It also, like Google calendar,
does not have a way to set todo dependencies or
recurring items.

My language would attempt to take the good parts
of each of these platforms and create a new DSL
that wraps Todo.txt with powerful calendar 
calculations. Effectively, I want it to tell me
what to do next and when to do it.

A DSL is appropriate because more imperative 
approaches would have difficulty processing
relations or indefinite repetition. Something like
"Every other Wednesday" would be easy to represent
in a DSL but very hard to represent as a class.

## Language domain

This DSL is in the domain of helping one manage their time.
Individuals will benefit from this language, especially
students who have many scheduled events and many recurring
due dates on tasks. I explained a lot of the background and
previous work in Motivations. As I said, I am even using,
or at least assuming, another DSL (Todo.txt) as a starting 
point for this 
project.

## Language design

This will be a text-based language that allows
slightly marked up statements to be interpreted 
as tasks with rich metadata. A program 
would look something like:

< Take out the trash @Home Daily after Dinner
< Dinner @Home Daily at 6pm
< Homework for DSLs before 9/9

This could then be made queryable through the DSL
through an API so that one could ask questions like 
"What can I do right now?" or "What do I need to do
today?". In theory, this interface could then be 
used to create a rich visual interface or just 
queried from the command line.

Programs for this language should follow the simple 
philosophy of Todo.txt, where it is fast and easy to
add tasks and the stored version of the program should
be a simple text file. Syntax should be incredibly 
intuitive and easy to remember. Anything else will add
too much overhead for people to want to use the 
language. 

As a intermediate representation, I think the structure
should be a sort of lazy generator of next events.
That way, it can take into account related and
repeating events easily.

## Example computations

The program takes in statements about events and
when they occur. It then stories these in an easily 
queryable manner.

Errors could come about in processing. However, these
should never be fatal. If something is not understood,
it should be treated a simply a task without whatever
metadata that failed to parse. It could be reasonable 
to print a warning, but this even is perhaps undesirable.
