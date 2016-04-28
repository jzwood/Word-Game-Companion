## [Word Game Companion (wgc)](http://jzwood.github.io/Word-Game-Companion/) ##

**wgc** is a super-mini web app that gives word-game enthusiasts tools for intelligent word searching.

### **how does it work?** ###

The power of **wgc** comes from constraining the bounds of a desired range with a binary search algorithm.

_What does this mean?_ Let's take a look:

Consider a small subset of the dictionary, just 20 consecutive words, from somewhere in the J's.

`jab, jabbed, jabber, jabbered, jabberer, jabberers, jabbering, jabbers, jabberwockies, jabberwocky, jabbing, jabiru, jabirus, jaborandi, jaborandis, jabot, aboticaba, jaboticabas, jabots, jabs`

Let's say we want to find any match that starts with `jabi` in the hopes of capitalizing on that sweet triple word score that just opened up (Scrabble reference).

The algorithm starts by considering the first word in the range, `jab`, and the last word in the range, `jabs`, and deduces that if any matches exist, they will appear alphabetically in between these two bounds. Since the range is 20 words long the algorithm splits it in half and looks at the 10th word, `jabberwocky`. Since `jabberwocky` comes alphabetically before `jabi` the algorithm specifies new bounds, with the lower bound equal to the 10th word and the upper the 20th.

It repeats this process until the range correctly matches the specified criteria. At this point it is simply an exercise of filtering results by length to get the final list of possible candidates. In this case: `jabiru` and `jabirus`.

### **that seems like too much work** ###

On the face of it, this seems like too many steps. Why not just look through the words until you find the ones you want?

Well, the dictionary I'm using for this app has 172,820 unique words in it. By successively dividing the dictionary in half we can peg the correct bounds after only 17 steps (because Log2(172,820) = 17.398), which is obviously way better (and faster) than the alternative!
