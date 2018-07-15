+++
title = "Between One and One Plus (Machine) Epsilon"
date = 2018-07-14T18:38:07-07:00
draft = true
summary = "A song of longing for a computing environment free of floating-point errors. To the tune of *Just Around the Riverbend* by Alan Menken, from the 1995 Disney film *Pocahontas*. Includes both solo and professor-student duet lyrics."

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["songs","computer-science"]
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
"Between One and One Plus Epsilon" is set to the music of "Just Around the Riverbend" by Alan Menken with lyrics by Stephen Schwartz. "Just Around the Riverbend" is from the 1995 Disney film *Pocahontas*. Alternative lyrics are by Susanne Bradley and Chen Greif.

Below the exceedingly lengthy educational footnotes, there's a slightly modified [professor-student duet version](#duet).

### Lyrics (solo version)

> What I love most about reals is  
> You’ll never list every single case  
> There’s always digits more than you’ll be showing<sup>[1](#reals)</sup>  
> Computers, I guess, can’t work with that  
> There’s only so much space  
> Using bits, we lose our chance of ever knowing

> What’s halfway to epsilon<sup>[2](#machEps)</sup>  
> Between one and one plus epsilon<sup>[3](#machEps2)</sup>    
> Bits binary, standard words<sup>[4](#word)</sup> of zero/one  
> For all your needs: doubles, ints, and floats  
> e, pi, root(3)  
> None of these are as they seem  
> Rounding errors intervene with code, mess up my code

> I see it in these random spikes<sup>[5](#roundoff)</sup>  
> That clutter my solution plot  
> Okay, perhaps my method makes them larger<sup>[6](#stable)</sup>   
> But just how can I compute things  
> As precisely as I ought  
> When I keep losing digits off my numbers?

> What’s halfway to epsilon  
> Between one and one plus epsilon  
> Bits binary, standard words of zero/one  
> I triple E<sup>[7](#ieee)</sup> shows us how it’s done  
> Reliably  
> But I can’t subtract a one  
> From one plus O of epsilon  
> Cancellation,<sup>[8](#ieee)</sup> that’s just wrong

> Roundoff errors amplified  
> It’s algebraic suicide<sup>[9](#suicide)</sup>  
> Should I change my step size<sup>[10](#step)</sup>  ?  
> Or has my work met its demise?  
> Or could I still increase machine precision  
> And get halfway to epsilon?



##### Footnotes
<a name="reals">1</a> See Georg Cantor's proof of the uncountability of the real numbers given in,
e.g., this [1994 article](https://www.maa.org/sites/default/files/pdf/upload_library/22/Ford/Gray819-832.pdf) by Robert Gray. Not only are there infinitely many real numbers (which would be enough to cause problems in a computing context, since we can obviously only represent finitely many different numbers), but
the infinite set is uncountable, meaning that we can't construct a one-to-one mapping from the natural numbers
to all the real numbers in an interval . The proof is by contradiction: we assume that we have a sequence
containing all numbers in $[a,b]$. Then Cantor's diagonal argument shows how we can construct a new number not
in the sequence by selecting digits from numbers in the sequence and then adding new digits at the end (hence 
"always digits more than you'll be showing").  
<a name="machEps">2</a> When we say epsilon we are, in this context, referring to *machine* epsilon,
and not an arbitrary small constant. Unfortunately, the scansion of "machine epsilon&" doesn't work with these
lyrics, so we've had to make do with the shorthand.  
<a name="machEps2">3</a> Machine epsilon (which we'll denote here by $\epsilon$) is the smallest number such
that $1 + \epsilon > 1$ in machine representation. Hence, anything between $1$ and $1 + \epsilon$ will be (inaccurately)
represented on a computer as being equal to $1$ -- so, this is a great, unknown space, much like "just around the 
riverbend" in this song's original, non-parody lyrics. For more information on machine epsilon (including an
experiment to compute it yourself), see the 
[Wikipedia article](https://en.wikipedia.org/wiki/Machine_epsilon).  
<a name="word">4</a> Some sources (e.g., [Ascher and Greif 2011](http://bookstore.siam.org/cs07/); 
also, see the corresponding
[lecture slides for chapter 2](https://pdfs.semanticscholar.org/presentation/0470/6dc02ee0f09b04a87ed9d1a0ff5ece44d2bb.pdf) use "IEEE standard word" to describe the 64-bit representation of a
number consisting of a sign bit, 11-bit exponent, and 52-bit fraction.  
<a name="roundoff">5</a> Roundoff errors tend to be non-smooth and very random-looking -- in contrast
with truncation errors (which are due to errors in the modeling and discretization of a problem).  
<a name="stable">6</a> Sometimes roundoff errors aren't due to the problem itself, but rather
with an unstable algorithm. See chapter 1 of [Ascher and Greif 2011](http://bookstore.siam.org/cs07/)
again for a discussion of the difference between ill-conditioning (the problem is badly behaved) and instability
(your algorithm makes roundoff errors blow up, even though the problem itself might be perfectly well-behaved).  
<a name="ieee">7</a> Refers to the [Institute of Electrical and Electronics Engineers](https://www.ieee.org/), originators of the [IEEE 754](https://ieeexplore.ieee.org/document/4610935/) -- the standard for floating-point computation used in many floating point units.  
<a name="cancel">8</a> Subtracting two nearby numbers -- that is, performing computations like $1 + O(\epsilon) - 1$ -- can lead to unacceptably high rounding errors because we lose many significant digits. For example, suppose we have two numbers with twelve significant digits, but the first nine are the same. If we subtract one from the other, we're left with just three significant digits, and this is irreversible! For more information on so-called "catastrophic cancellation", including some ways to avoid it, consult any standard numerical analysis text (for example, chapter 2 of [Ascher and Greif 2011](http://bookstore.siam.org/cs07/)).  
<a name="suicide">9</a> Shout-out to the textbook of [Elman, Silvester and Wathen 2005](https://global.oup.com/academic/product/finite-elements-and-fast-iterative-solvers-9780199678808?cc=ca&lang=en&) for exposing me to the truly excellent phrase "algebraic suicide."   
<a name="step">10</a> Several types of numerical method rely on some kind of "step" (either in space or in time), the size of which can adversely affect the stability of the method. But it's most commonly of concern in the solution of ordinary and partial differential equations -- see, e.g., [Kraaijevanger et. al. 1987](https://core.ac.uk/download/pdf/82036576.pdf).

### <a name="duet">Lyrics (duet version)</a>
> [**STUDENT**] What I love most about reals is  
> You’ll never list every single case  
> There’s always digits more than you’ll be showing
   
> [**PROF**] Computers, you know, can’t work with that  
> There’s only so much space  

> [**STUDENT**] But with bits, we lose our chance of ever knowing  
> What’s halfway to epsilon  
> Between one and one plus epsilon 

> [**BOTH**] Bits binary, standard words of zero/one  
> For all your needs: doubles, ints, and floats  

> [**STUDENT**] e, pi, root(3)  
> None of these are as they seem  
> Rounding errors intervene with code, mess up my code  
> [*student hands professor her work*]  
> [**STUDENT**] I see it in these random spikes  
> That clutter my solution plot  

> [**PROF**] I think perhaps your method makes them larger  

> [**STUDENT**] Well just how can I compute things  
> As precisely as you want  
> When I keep losing digits off my numbers?  
> What’s halfway to epsilon  
> Between one and one plus epsilon  

> [**BOTH**] Bits binary, standard words of zero/one  
> I triple E shows us how it’s done  

> [**PROF**] Reliably  
> But don't you subtract a one  
> From one plus O of epsilon  
> Cancellation, that’s just wrong  
> [*professor shakes his head at student's work*]  
> [**PROF**] Roundoff errors amplified  
> It’s algebraic suicide  
> [*professor walks off*]

> [**STUDENT**] Should I change my step size?  
> Or has my work met its demise?  
> Or could I still increase machine precision  
> And get halfway to epsilon?