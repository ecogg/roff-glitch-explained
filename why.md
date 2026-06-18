# Why Github says that a repository contains the "ROFF" language in it, when it really doesn't.

There are many files that this could happen with, but here is a common example: The "`.7z`" file
---
The `.7z` file isn't being recognized by GitHub as a valid binary 7-Zip archive, or that it's actually a text file that just happens to have a `.7z` extension.

GitHub's language detector (Linguist) then tries to guess what kind of text it is and ends up classifying it as ROFF, which can change up the language statistics if the file is large enough. For example, if your repository contains 
* 10 MB of JavaScript, TypeScript, and Python
* 15 MB of a misclassified `.7z` file
then GitHub might report somethubg like:
* Roff: 44%
* JavaScript: 26%
* TypeScript: 24%
* Python: 6%
even though there isn't a single actual Roff source file in the repo.

If it's your repository and you want to fix the language stats, you can add a `.gitattributes` file:
