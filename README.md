## Word Game Companion ##

**WGC** is a super-mini web app that gives word-game enthusiasts tools for intelligent word searching.

### **how does it work?** ###

The power of WGC comes from constraining the bounds of a search range with an binary search algorithm.

What does this mean? Let's take a look:

Consider small subset of the dictionary, just 20 consecutive words, from somewhere in the J's.

`jab, jabbed, jabber, jabbered, jabberer, jabberers, jabbering, jabbers, jabberwockies, jabberwocky, jabbing, jabiru, jabirus, jaborandi, jaborandis, jabot, aboticaba, jaboticabas, jabots, jabs`

Let's say we want to find any match that starts with `jabi` in the hopes of capitalizing on that sweet tripple word score that just opened up.

The algorithm starts by considering the first word in the range, `jab`, and the last word in the range, `jabs`, and deduces that if any matches exist, they will appear alphabetically in between these two bounds. Since the range is 20 words long the algorithm splits it in half and looks at the 10th word, `jabberwocky`. Since `jabberwocky` comes alphabetically before `jabi` the algorithm specifies new bounds, the 10th word and the 20th.

It repeats this process until range correctly matches the specified criteria. At this point it is simply an excercise of filtering results by length to get the final list of possible candidates. In this case: `jabiru` and `jabirus`.

### **that seems like too much work** ###

On the face of it, this seems like a lot of step. Why not just look through the words until you find the ones you want? The dictionary I'm using for this app has 172,820 unique words. You would never expect a person to do this much work, don't ask your computer to either. By dividing the dictionary by half we can deduce the correct bounds after only 17 steps (because Log2(172,820) = 17.398)!
