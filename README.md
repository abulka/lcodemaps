# Literate Code Maps

*Diagramming Methodology Specification - version 1.0 - Author: Andy Bulka*

Literate Code Maps are diagrams which help programmers understand the structure and behaviour of source code. 

Code Map diagrams differ from UML diagrams in that they 
focus on real source code fragments and lots of 
rich-text formatted story-telling narrative. 
They combine class and sequence diagrams into the same
diagram, offering step by step numbering to follow the behaviour of a use case story. 

> Literate Code Maps - are not to be confused with the Code Map feature of Visual Studio Enterprise. Literate Code Maps are a free and open diagramming methodology. Visual Studio Code Maps is an interactive code relationship analysis tool reserved for Microsoft languages and customers.

# Quick Intro

## Maximize data density

As [Tuft](https://www.google.com/search?sxsrf=ACYBGNS1EpNz4CfrqW-z9eFY1ZGPhFiGFQ%3A1574306638649&ei=TgPWXbChJ--CrtoPldyooAE&q=tufte+principles&oq=tufte+principles&gs_l=psy-ab.3..35i39l2j0l3.18998.18998..20000...0.4..0.160.160.0j1......0....1..gws-wiz.......0i71.p3-NlWLJeD4&ved=0ahUKEwiwgNufrfrlAhVvgUsFHRUuChQQ4dUDCAs&uact=5) 
says: *"Visual representations of data must tell the truth... Above all else show data... Maximize data density"*.
For programmers, data means source code including variables, data structures, sample values and payloads. 

The traditional UML class 

![basic uml](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/basic-uml.puml&fmt=svg)

becomes data rich and full of useful detail

![basic code map](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/basic-codemap.puml&fmt=svg)

A diagram need only list the code fragments that are required to tell a particular use case **story**.

## Numbered steps

To avoid being lost in abstraction, Literate Code Maps rely on textual narrative and story telling,
as well as numbered steps for the reader to follow. 
A diagram should have a starting point and a series of steps to follow, to tell a use case story:

![numbered steps code map](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/numbered-steps.puml)

Notice the box "H" which represents a HTML file, let's talk about this more now.

# Boxes represent any namespace

In Literate Code Maps diagrams, boxes represent any Namespace - not just Classes.
Even files can be represented. Code Map diagrams boxes can represent:

* classes
* packages
* functions
* namespaces
* files of any type e.g. HTML
* Python module files
* sub-systems
* any architectural or deployment grouping
* etc.

Code Map diagrams boxes are not tied to 
Object Oriented paradigms, and are thus more universal and useful.

Instead of using square boxes, you might want to use different shapes e.g. https://blog.anoff.io/puml-cheatsheet.pdf shows all the component types you can use.

## HTML file boxes

For example, 
HTML files with fragments of HTML markup can be represented - great for showing how code interacts with HTML templating. 

![html file code map](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/html-example.puml)

Javascript code fragments residing in the HTML file
can be represented - see above diagram.

## Functional Languages

Files containing *just* functions and variables (no classes) can be represented as boxes in a way that makes them "look like" classes. For example, the Python file "utils.py"

```python
x = 1
y = 2
def fred(): 
    pass
```

turns into 

![Python module as pseudo class](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/python-module.puml)

which looks like a class, even though there is not a Class in sight!

Thus, Python programmers with modules (files) containing
only variables and functions will be able to visualise their
codebase.

> It is recommended that boxes have a "stereotype" indicating what kind of box it is. For example for a Python module we stamp it with an "M" which stands for module as well as spell out the word "MODULE" and the path to the file. For HTML files the icon stereotype should be "H" etc.

This representational idea is also a boon for Javascript programmers who
may have lots of variables and functions, and no classes.  Together with the ability
to visualise HTML files as boxes, web developers now have the ability to model. 

This modelling idea applies to other functional programming languages.  
Ideally the data / behaviour separation in boxes should be followed.

