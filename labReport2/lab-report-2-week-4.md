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
When initially running the code on the file [testFR_filePt3.md](https://github.com/fnriv/markdown-parser/blob/main/testFR_filePt3.md), the output for the file was `[coolmath, https://twitter.com/?lang=en]` when it should have been `[https://www.coolmathgames.com/, https://twitter.com/?lang=en]`.

This incorrect output, or **_symptom_**, was due to the java file only looking for the symbols "[", "]", "(", and ")". In this case, the **_failure-inducing input_** was that when brackets or parentheses were outside of the actual link format, it would recognize it to be part of the link syntax and proceed to find the nearest pair of parentheses.

To fix this, I made the java file look for the following strings of symbols: "[", then "](", then ")", as shown in the code change diffs below. It shows how I used print statements to find the errors, then how I changed the code to fix the bug. 

![example 1 pt 1](ex1pt1.png)
I added testing print statments as well as changed the symbols the code searched for (`closeBracket` was joined with `openParen` to be `closeBracketAndOpenParentheses`).
![example 1 pt 2](ex1pt2.png)
I cleaned up my code to take out the testing print statments; but realized my indexing for `closeBracketAndOpenParentheses` was incorrect: the output included the "(" in the output for the links.
![example 1 pt 3](ex1pt3.png)
I fix my indexing for `closeBracketAndOpenParentheses` so that the print statment will not include the "(" in the list.

After making these changes, the output was correct and the symptom was gone, meaning that this bug was fixed!

