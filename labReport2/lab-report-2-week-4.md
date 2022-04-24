# week 4 - lab report 2
## by faith rivera
### april 22, 2022

--- 

## debugging code 

  
<p align="center">
  <img src="https://media.giphy.com/media/l0HU99Q4OEUCjTl3W/giphy.gif" width="2800">
</p>

Let's face it: bugs in code are inevitable. We often must recheck our work and fix issues in our code to make sure it runs as expected.

The following blog post will show examples of analyzing code and its failure-inducing inputs to find bugs and fix them. 

All fixes were done on a java file called **MarkdownParse.java** (original unedited code [here](https://github.com/nidhidhamnani/markdown-parser/blob/main/MarkdownParse.java)), whose purpose is to print a list of all the links in a markdown file that are formatted with Markdown link syntax. For instance, when we have this Markdown file code:

```
# Title
[link1](https://something.com)
[link2](some-thing.html)
```
Then MarkdownParse.java should print the following when run:
```
[https://something.com, some-thing.html]
```
### example one: making sure [] and () are connected for link format
