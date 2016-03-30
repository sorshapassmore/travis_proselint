I needed this tutorial already in 2006, when I started experimenting with Boost.Graph. More specifically, I needed a tutorial that:

• Orders concepts chronologically

• Increases complexity gradually

• Shows complete pieces of code

What I had were the book [siek2001boost] and the Boost.Graph website, both did not satisfy these requirements. 

This tutorial is aimed at the beginner programmer. This tutorial is intended to take the reader to the level of understanding the book [siek2001boost] and the Boost.Graph website require. It is about basic graph manipulation, not the more advanced graph algorithms. 

This tutorial is intended to be as verbose, such that a beginner should be able to follow every step, from reading the tutorial from beginning to end chronologically. Especially in the earlier chapters, the rationale behind the code presented is given, including references to the literature. Chapters marked with '▶' are optional, less verbose and bring no new information to the storyline. 

This tutorial is intended to be as repetitive, such that a beginner can spot the patterns in the code snippets their increasing complexity. Extending code from this tutorial should be as easy as extending the patterns.

In the index, I did first put all my long-named functions there literally, but this resulted in a very sloppy layout. Instead, the function 'do_something' can be found as 'Do something' in the index. On the other hand, STL and Boost functions like 'std::do_something' and 'boost::do_something' can be found as such in the index.

For every concept, I will show

• a function that achieves a goal, for example `create_empty_undirected_graph'

• a test casetest case of that function, that demonstrates how to use the function, for example `create_empty_undirected_graph_test'

All coding snippets are taken from compiled and tested C++14 code. I chose to use C++14 because it was available to me on all local and remote computers. Next to this, it makes code even shorter then just C++11. 

I use the coding style from the Core C++ Guidelines. At the time of this writing, the Core C++ Guidelines were still in early development, so I can only hope the conventions I then chose to follow are still Good Ideas.

It is important to add comments to code. In this tutorial, however, I have chosen not to put comments in code, as I already describe the function in the tutorial its text. This way, it prevents me from saying the same things twice.

It is good to write generic code. In this tutorial, however, I have chosen my functions to have no templated arguments for conciseness and readability. For example, a vertex name is std::string, the type for if a vertex is selected is a boolean, and the custom vertex type is of type `my_custom_vertex'. I think these choises are reasonable and that the resulting increase in readability is worth it.

I enjoy to show concepts by putting those in (long-named) functions. These functions sometimes border the trivial, by, for example, only calling a single Boost.Graph function. On the other hand, these functions have more English-sounding names, resulting in demonstration code that is readable. Additionally, they explicitly mention their return type (in a simpler way), which may be considered informative.

Due to my long function names and the limitation of ≈50 characters per line, sometimes the code does get to look a bit awkward. I am sorry for this.

I prefer to use the keyword auto over doubling the lines of code for using statements. Often the `do' functions return an explicit data type, these can be used for reference. Sometime I deduce the return type using decltype and a function with the same return type. When C++17 gets accessible, I will use `decltype(auto)'decltype(auto). If you really want to know a type, you can use the `get_type_name' function (chapter [sub:get_type_name]). 

On the other hand, I am explicit in the namespaces of functions and classes I use, so to distinguish between types like `std::array' and `boost::array'. Some functions (for example, `get'get) reside in the namespace of the graph to work on. In this tutorial, this is in the global namespace. Thus, I will write `get', instead of `boost::get'boost::get does not exist, as the latter does not compile.

I try to use STL algorithms wherever I can. Also you should prefer algorithm calls over hand-written for-loops ([stroustrup1997] chapter 18.12.1, [meyers2005effective] item 43). Sometimes using these algorithms becomes a burden on the lines of code. This is because in C++11, a lambda function argument (use by the algorithm) must have its data type specified. It may take multiple lines of `using' statements being able to do so. In C++14 one can use `auto' there as well. So, only if it shortens the number of lines significantly, I use raw for-loops, even though you shouldn't.

The functions I develop in this tutorial are re-used from that moment on. This improves to readability of the code and decreases the number of lines.

All functions in this tutorial are tested to compile using Travis CI in both debug and release mode. 

All functions in this tutorial are tested, using the Boost.Test library. Travis CI calls these tests after each push to the repository.

The code, as well as this tutorial, can be downloaded from the GitHub at www.github.com/richelbilderbeek/BoostGraphTutorial.
