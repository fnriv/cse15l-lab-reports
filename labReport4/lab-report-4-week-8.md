# week 8 - lab report 4
## by faith rivera
### may 22, 2022

--- 

## editing code (markdown parser)


<p align="center">
  <img src="https://cdn.dribbble.com/users/330915/screenshots/3587000/10_coding_dribbble.gif" width="2800">
</p>

This week, we will be comparing implementations of `MarkdowmParse.java` based on 3 snippets of Markdown code. I will be reviewing [my repo](https://github.com/fnriv/markdown-parser) as well as the repo for [team Echidnas](https://github.com/AlexVazquez19/markdown-parser-echidnas).

## Snippet 1

When I create a Markdown file of Snippet 1, the preview of the file looks like this:
![Snippet 1 Preview](Snippet1.png)

This means that based on the preview, the expected output of a `MarkdownParse.java` test would be the array **[google.com]**. The Google link is recognized from the second google link in the file.

**Test and results for Snippet 1 in my own `MarkdownParseTest.java`:**
![My test for Snippet 1 and results](S1Faithtest.png)

**Test and results for Snippet 1 in team Echidnas `MarkdownParseTest.java`:**
![Echidnas test, Snippet 1](S1Echidnastest.png)

As evidenced by the stack traces, both tests did not pass. 

I think there is a small code change that will allow links to be formatted in grave accents within the brackets. The code can be fixed to check if one of the grave marks is before the brackets (meaning that its formatting is prioritized), so that if it is, it will focus on the code format instead of the link format.

---

## Snippet 2

When I create a Markdown file of Snippet 1, the preview of the file looks like this:
![Snippet 2 Preview](Snippet2.png)

This means that based on the preview, the nested link will be prioritized. However, parentheses sometimes hold special meaning, so because they might need to be encoded they will not always be accepted as a valid link. Thus, link 2 should not be added to the returned array when the file is parsed through (which is also due to the nested parentheses).

**Test and results for Snippet 2 in my own `MarkdownParseTest.java`:**
![Faith's test, Snippet 2](S2Faithtest.png)

**Test and results for Snippet 1 in team Echidnas `MarkdownParseTest.java`:**
![Echidnas test, Snippet 2](S2Echidnastest.png)

As evidenced by the stack traces, both tests did not pass, for different reasons. Both accept `a.com((` as a link, but the Echidnas' `MarkdownParse.java` does not allow for the prioritization of nested links or brackets inside of the first link (since there is an extra `]` separating the first `]` from the parentheses).

I do not think it would be possible to have a short-code fix for this snippet for the nested brackets or parentheses. Although we can check if there is space in between the brackets and parentheses, checking for the nested links would require more variables tracking whether or not a link is completed within a link bracket. Furthermore, you would have to account for triple or quadruple nesting or more.

---

## Snippet 3