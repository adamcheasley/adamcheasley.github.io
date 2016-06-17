# Code review

I've been working with code review exclusively for about 3 years now. This means all code goes through a pull request, without exception. I have noticed though that the quality of code review can vary quite a bit, so I thought I'd write about what I try to do when reviewing someone else's code.

First of all, the most important thing is; Don't take it personally. I see this a lot, especially with developers who are new to code review. Any comment or suggestion is not meant as a personal attack. We are all in this together, and we both want the best code possible.

Another pitfall I see happen, even to experienced developers, is that the reviewer just makes superficial comments regarding style. The first thing I always try to do is review the meaning of the code, not the style. 
- What is this code doing?
- Look for side effects.
- What has been removed? Is that going to be ok?
- Can I spot an edge case that hasn't been tested?

Only after I've answered these questions will I then attempt to look at the style of the code and where it could be cleaned up. 

Checkout the code, run it yourself.

