# Code review

I've been working with code review for about 3 years now. In my current position, all code goes through a pull request, without exception. Over the years and different projects, I have noticed though that the quality of code review can vary quite a bit, so I thought I'd write about what I try to do when reviewing someone else's code.

First of all, the most important thing is; Don't take it personally. I see this a lot, especially with developers who are new to code review. Any comment or suggestion is not meant as a personal attack. We are all in this together, and we both want the best code possible and for the code to follow known best practices.

Another pitfall I see, even from experienced developers, is that the reviewer just makes superficial comments regarding code style. The first thing I always try to do is review the meaning of the code, not the style. Attempt to grok the fix/feature in its entirety:
- What is this code doing?
- Are there any hidden side effects?
- What has been removed? Is that going to be ok?
- Can I spot an edge case that hasn't been tested?

Only after I've answered these questions will I then attempt to look at the style of the code and where it could be cleaned up. 

For really large features, there's really nothing better than to checkout the code and run it yourself. This can really help with understanding the flow of the code as a whole, as you understand the outcome. This might also enable you to spot bugs that just reading the code might miss.

