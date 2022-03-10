# Lab Report #5 - Week 10

* For this lab report, I will be comparing the results of two different versions of markdown parse on a large set of test files. 
    * In order to find the difference between the results,
    I ran a bash for loop and appended the results to a text file called `results.txt`. Then, I used the `diff` command to compare the two separate files. I've chosen two of the different test cases to compare.

    ## Test #1

    * The first test file I will be comparing is Test File #495, that contains an regular text between the parentheses after the closed bracket. Here are the outputs of both implementations:
        * My output: `[foo(and(bar]`
        * Other output: `[foo(and(bar))]`
    * The correct output should be: `[]` since there is no valid link in the test file. Therefore, neither implementation returns the correct output.

    * For the other implementation, it returns everything within the parentheses, however, it never checks whether the text is a valid link. In order to do this, we would have to parse the substring within the parentheses and make sure there aren't any invalid characters, make sure there is a domain, etc. If so, it should simply skip the iteration and increment the index. There isn't any code that should necessarily be fixed, but there is code that should be added to the existing implementation.

    ## Test #2

    * The second test I will be comparing is Test File #580 that contains an image with an invalid link. Here are the outputs of both implementations: 

        * My output: `[]`
        * Other output: `[/url]`

    * The correct output should be `[]` since the file contains an image as well as an invalid image link. Therefore, my implementation is correct while the other is incorrect.

    * In the other implementation, there is never a check for an exclamation mark right before the first open bracket to distinguish between an image link versus a regular link. Additionally, this corresponds to the previous test issue since this implementation isn't checking for a valid link between the parentheses. Both issues need to be fixed in order to resolve this bug.

