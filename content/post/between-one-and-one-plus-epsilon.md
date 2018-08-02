+++
title = "Between One and One Plus (Machine) Epsilon"
date = 2018-07-16T18:38:07-07:00
draft = false
summary = "(Parody song.) A song of longing for a computing environment free of floating-point errors. To the tune of *Just Around the Riverbend* by Alan Menken, from the 1995 Disney film *Pocahontas*."

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["songs","computer-science-songs"]
categories = []

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
# Use `caption` to display an image caption.
#   Markdown linking is allowed, e.g. `caption = "[Image credit](http://example.org)"`.
# Set `preview` to `false` to disable the thumbnail in listings.
[header]
image = ""
caption = ""
preview = true

+++
"Between One and One Plus Epsilon" is set to the music of "Just Around the Riverbend" by Alan Menken with lyrics by Stephen Schwartz. "Just Around the Riverbend" is from the 1995 Disney film *Pocahontas*. Alternative lyrics are by Susanne Bradley, with thanks to Chen Greif for providing cancellation-related suggestions.

### Lyrics

> What I love most about reals is  
> You’ll never list every single case  
> There’s always digits more than you’ll be showing[^1]  
> Computers, I guess, can’t work with that  
> There’s only so much space  
> Using bits, we lose our chance of ever knowing

> What’s halfway to epsilon[^2]  
> Between one and one plus epsilon[^3]   
> Bits binary, standard words[^4] of zero/one  
> For all your needs: doubles, ints, and floats  
> e, pi, root(3)  
> None of these are as they seem  
> Rounding errors intervene with code, mess up my code

> I see it in these random spikes[^5]  
> That clutter my solution plot  
> Okay, perhaps my method makes them larger[^6]  
> But just how can I compute things  
> As precisely as I ought  
> When I keep losing digits off my numbers?

> What’s halfway to epsilon  
> Between one and one plus epsilon  
> Bits binary, standard words of zero/one  
> I triple E[^7] shows us how it’s done  
> Reliably  
> But I can’t subtract a one  
> From one plus O of epsilon  
> Cancellation,[^8] that’s just wrong

> Roundoff errors amplified  
> It’s algebraic suicide[^9]  
> Should I change my step size?[^10]   
> Or has my work met its demise?  
> Or could I still increase machine precision  
> And get halfway to epsilon?


[^1]: This refers vaguely to Georg Cantor's proof that the real numbers are uncountably infinite -- see, e.g., [Gray 1994](https://www.maa.org/sites/default/files/pdf/upload_library/22/Ford/Gray819-832.pdf). The proof is by contradiction: we assume that we have a sequence containing all numbers in an interval $[a,b]$. Then Cantor's diagonal argument shows how we can construct a new number in $[a,b]$ that's not in the sequence by selecting digits from numbers in the sequence and then adding new digits at the end (hence "always digits more than you'll be showing").  
[^2]: When we say epsilon we are, in this context, referring to *machine* epsilon, and not an arbitrary small constant. Unfortunately, the scansion of "machine epsilon" doesn't work well with this song, so we've had to make do with the shorthand. (Another option would have been to try to make "unit roundoff" work, but that sounds less poetic than "epsilon." It also would have denied us our repeatedly used semi-rhyme between "epsilon" and "one," and that would just be ignorant.)  
[^3]: Machine epsilon (which we'll denote here by $\epsilon$) is the smallest number such that $1 + \epsilon$ is greater than $1$ in machine representation. Hence, anything between $1$ and $1 + \epsilon$ will be (inaccurately) represented on a computer as being equal to $1$ -- so, this is a great, unknown space, much like "just around the  riverbend" in this song's original, non-parody lyrics. For more information on machine epsilon (including an experiment to compute it yourself), see the  [Wikipedia article](https://en.wikipedia.org/wiki/Machine_epsilon).  
[^4]: Some sources (e.g., [Ascher and Greif 2011](http://bookstore.siam.org/cs07/))  use "IEEE standard word" to describe the standard 64-bit representation of a number, which consists of a sign bit, 11-bit exponent, and 52-bit fraction. Also see [Overton 2001](https://epubs.siam.org/doi/book/10.1137/1.9780898718072) for details and examples.  
[^5]: Roundoff errors tend to be non-smooth and random-looking (though they are, of course, not actually random). That's quite different from truncation errors, which are due to errors in the modeling and discretization of a problem (and tend to be smoother and more predictable).  
[^6]: Sometimes roundoff errors aren't due to the problem itself, but rather to an unstable algorithm. See chapter 1 of [Ascher and Greif 2011](http://bookstore.siam.org/cs07/) again for a discussion of the difference between ill-conditioning (when the problem is badly behaved) and instability (when your algorithm makes roundoff errors blow up, even though the problem itself might be perfectly well-behaved).  
[^7]: Refers to the [Institute of Electrical and Electronics Engineers](https://www.ieee.org/), originators of the [IEEE 754](https://ieeexplore.ieee.org/document/4610935/): the standard for floating-point computation used today in most floating point units.  
[^8]: Subtracting two nearby numbers -- that is, performing computations like $(1 + O(\epsilon)) - 1$ -- can lead to unacceptably high rounding errors because we lose many significant digits. For example, suppose we have two numbers with twelve significant digits, but the first nine are the same. If we subtract one from the other, we're left with just three significant digits, and this is irreversible! For more information on so-called "catastrophic cancellation," including some ways to avoid it, consult a numerical analysis text (for example, chapter 2 of [Ascher and Greif 2011](http://bookstore.siam.org/cs07/)).  
[^9]: Shout-out to the textbook of [Elman, Silvester, and Wathen 2014](https://global.oup.com/academic/product/finite-elements-and-fast-iterative-solvers-9780199678808?cc=ca&lang=en&) for coining the truly excellent phrase "algebraic suicide" on p. 131. (It was actually "linear algebraic suicide," but close enough.)   
[^10]: Several types of numerical method rely on some kind of "step" (either in space or in time), the size of which can affect the stability of the method. It's most commonly of concern in the solution of ordinary and partial differential equations -- see, e.g., [Kraaijevanger et. al. 1987](https://core.ac.uk/download/pdf/82036576.pdf).