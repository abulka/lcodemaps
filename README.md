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

![numbered steps code map](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/numbered-steps.puml&fmt=svg)

Notice the box "H" which represents a HTML file, let's talk about this more now.

## Cross References

Use of cross reference numbers in the diagram handle the multi-dimensional relationships involved in thinking about and explaining software, and its cross cutting concerns.

Cross references are red numbers e.g. `22` or `23` with destinations as e.g. `#22`.

Lines between boxes are reserved for function calls.

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

## HTML files as Boxes

For example, 
HTML files with fragments of HTML markup can be represented - great for showing how code interacts with HTML templating. 

![html file code map](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/html-example.puml&fmt=svg)

Javascript code fragments residing in the HTML file
can be represented - see above diagram.

## Boxes of Functions (no classes)

Files containing *just* functions and variables (no classes) can be represented as boxes in a way that makes them "look like" classes. For example, the Python file "utils.py"

```python
x = 1
y = 2
def fred(): 
    pass
```

turns into 

![Python module as pseudo class](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/python-module.puml&fmt=svg)

which looks like a class, even though there is not a Class in sight!

Thus, Python programmers with modules (files) containing
only variables and functions will be able to visualise their
codebase. The online diagramming tool [GitUML](https://www.gituml.com) already supports reverse engineering Python modules into boxes in this way.

> It is recommended that boxes have a "stereotype" indicating what kind of box it is. For example for a Python module we stamp it with an "M" which stands for module as well as spell out the word "MODULE" and the path to the file. For HTML files the icon stereotype should be "H" etc.

This representational idea is also a boon for Javascript programmers who may have lots of variables and functions, and no classes.  Together with the ability to visualise HTML files as boxes, web developers now have the ability to model. 

> This modelling idea applies to other functional programming languages.  Ideally the data / behaviour separation in boxes should be followed.

# Examples

Here are some more examples of literate code maps.

![code map example 01](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg)

## More Complex Example

![code map example 02](https://raw.github.com/abulka/lcodemaps/master/images/example-02.svg)

Larger diagrams can be zoomed into.  If they are rendered as SVG images then there is no loss of detail.  All the diagrams in this article are SVG and can be clicked on and zoomed into.

The public PlantUML server used to render these code maps has a limit on the size of the diagrams it produces. You can easily set up your own PlantUML server locally which not only is faster, but can generate much larger diagrams before clipping them. See the [PlantUML Server Documentation](http://plantuml.com/server) and you may also find the helpfile in [Pynsource](www.pynsource.com) useful as it contains more detailed local PlantUML server install instructions that I give my Pynsource (Python UML tool for Mac, Windows, Linux) customers.

# Building your own Literate Code Maps

By building a Code Map of a particular use case store of  code base, you will not only grow to understand the code, but you can refer to your code map in the future, and share it with colleagues.

It is recommended to use [PlantUML](http://plantuml.com/) markup to generate your Literate Code Map diagrams. 

To create code subsections in boxes/classes, use the following markdown sytax e.g.:

    .. def myfunction(param1, param2): ..

To include code fragments inside classes, 
define some handy macros then use the following markdown sytax e.g.:

    !$code = "<color:royalBlue><size:14>"

then simply add the word `codeb` before each line of your code fragment. Use spaces to indent, or `\t`.

    $code for i in range(100):
    $code     print(i)

View the [examples directory](https://github.com/abulka/lcodemaps/tree/master/plantuml) for the full source code to the code maps used in this article.

Please also check out 
[GitUML](https://www.gituml.com) which supports building UML and Literate Code Map diagrams online, using a combination of source code reverse engineering and PlantUML markup.

# History - Why Code Maps?

When I have encountered a huge codebase, or an old project I wrote myself, or just a complex code area - I typically trace out and make notes as I read the code. How many programmers do something similar?  Here is an example of a hand-crafted literate code map:

![hand_crafted_early_code_map](https://raw.github.com/abulka/lcodemaps/master/images/handcrafted-code-map-andy.png)

Over the years, this has developed into a methodology of sorts. Then I started copying and pasting code fragment screenshots into a paint tool - why re-write when you can copy and paste!  I connected the boxes with lines and added narrative text comments. This was a *little* more professional, but gee - I wish I had auto-layout so that I could squeeze and rearrange the diagram when I discovered new things. Here is an example of an old hand built digital literate code map diagram:

![screenshot_crafted_early_code_map](https://raw.github.com/abulka/lcodemaps/master/images/handcrafted-screenshot-based-code-map-andy.jpg)

Then I moved on to using PlantUML markup code - allowing the diagrams and notes to be automatically laid out, be pretty to look at and maintainable.

![code map example 01](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg)

# Tufte

Whilst I knew my literate code maps worked (for me, personally) - I didn't have any research or scientific backing for them. 

Then I thought of Edward Tuft's visualisation work, which I have been a fan of for a long time. Sure enough, his ideas on density, detail, rich formatting, use of icons and small graphics at any place where you would put text - are all consistent with literate code maps. Especially the idea of combining detail and abstraction in the same diagram - the boxes are the abstraction and the code is the detail.

I hope to tie more of Tufte's insights into the Literate Code Map methodology, as well as draw from the vast field of [Information Visualization](https://en.wikipedia.org/wiki/Information_visualization).

> Wikipedia says “Information visualization presumes that "visual representations and interaction techniques take advantage of the human eye’s broad bandwidth pathway into the mind to allow users to see, explore, and understand large amounts of information at once. Information visualization focused on the creation of approaches for conveying abstract information in intuitive ways.

I also like many of the ideas of [C4 architecture notation](https://c4model.com) e.g. each line being labelled and having a direction. C4 also has some good criticisms of UML in the main C4 video, which I encourage people to watch.

# UML

Literate Code Maps are not UML.  

Code Maps are more detailed and can actually be used to debug code and add features, because they contain code fragments which are relevant to day to day programmers. They contain narrative, story telling text - which leverages how we learn. They also take advantage of the human eye’s broad bandwidth pathway to take in visual information.

UML *is* useful when judiciously used, but most UML diagrams tend to be too abstract to actually be helpful to a programmer.  As I write in [my blog](http://www.andypatterns.com/), 

> UML (Unified Modelling Language) has fallen out of favour in the last decade and now tends to only get used in the most basic of ways.  Sketches on whiteboards to commuicate class relationships or code execution sequences. Or simple diagrams in documentation and designs.  Nobody uses the complex notations of UML 2, because digramming cannot keep up with the myriad programming techniques and paradigms of 2018 - code is simply not reducible to visual information.

I think that there are a limited numbers of cases where UML diagrams might be helpful:
- whiteboard communication
- database modelling
- big picture architecture diagrams (also see [C4 architecture notation](https://c4model.com))
- class diagrams of complex class relationships
- representing design patterns
- sequence diagrams of certain code behaviours
- state diagrams are also sometimes useful

UML lacks normal human, tutorial-like, step by step narrative textual storytelling and code level detail.  Staring at at a UML diagram typically leaves you wanting much more detailed information. Staring at source code typically leaves you wanting a diagram of relationships and context. Literate Code Maps are an attempt to solve this problem.

# Contributing

If you wish to contribute to this diagramming specification I am open to pull requests. Let's make *Literate Code Maps* something that brings practical, useful visualisation technology back into software development, without the old UML baggage.
