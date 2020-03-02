# The Gist

Lecturer Slide: https://github.com/SSQ/Coursera-Stanford-Divide-and-Conquer-Sorting-and-Searching-and-Randomized-Algorithms/blob/master/Lecture%20Slides/2.1-algo1-aa-gist_typed.pdf
Status: Completed
Video Link: https://youtu.be/l-cNaKGc-yY

### The merge sort is 6n*log2(n)+6n. Why 6n is low-order term in the case mentioned in the video and 6 is constant factor? Do these terms have concrete definition?

- ***x*** has order of magnitude 1, since it can be written as ***x1***, and ***x2*** has order 2 - the order of magnitude is equal to the power of the variable in the term.
- f(x) is a lower order than g(x) if f(x) < g(x) as x tends to infinity
- f(n) = 6n is a lower order than g(n) = 6n*log2(n) by just substituting some really large value for n

> a lower-order term is just any term which is of a lower order than some other term.

- "Factor" is a term in multiplication. For `6n`, `6` and `n` are factors.

> A constant factor is simply anything that doesn't depend on the input parameter(s) (which is `n` in this case).

- Here, regardless of what we make `n`, `6` will always stay `6`, so it's constant.

[What is constant factors and low-order term in algorithms?](https://stackoverflow.com/questions/22614585/what-is-constant-factors-and-low-order-term-in-algorithms)