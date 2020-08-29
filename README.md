# Jupyter (iPython) Notebooks

A repository of -- 🤮🤮🤮 -- Jupyter (iPython) Notebooks.

Look if you must. Use if you ___must___. But if you're not being forced by financial holds, job security, or threats of violence (physical, emotional, or psychological), then please please please leave this place and never return.

If you're offended by our rants and ravings; we apologise. We mean no offense, only warning. Jupyter (iPython) Notebooks are _not_ how you write good, reliable, robust software, and they are _not_ going to help you anywhere near as much as you think in R&D. Maaaaaybe they're ok for prototyping, but that's like saying maybe a shoe is ok as a hammer.

Nobody wants to live in a house where all the nails were driven by shoes.

At the very least, though, besides the oft-ignored ravings of lovable fool, you'll find some shoe-hammered house Notebooks of our own, for example or reference, or learning or burning. Just, please, don't spread this disease. Write modules and packages and functions and classes! Save yourself! Leave this place!

![Thanks, I Hate It](./imgs/LOTR-Gandalf-FlyYouFools.gif)

## Friends Don't Let Friends Use Jupyter Notebooks

This is a personal preference -- with _reasons_ -- so feel free to ignore us, but we _strongly_ suggest that you __do not__ use __Jupyter Notebooks__ for Python development. The quick list of reasons are:

- Notebook code is stored in JSON files that are horrendous to read and `diff`.
- Notebooks need an HTML Generator ("renderer") to view them "properly", and a specialised runtime HTML editor to modify them "properly" -- yes, this is all packaged up with the `jupyter-labs` runtime and a Web-browser, but the fact still remains that you need them both.
- Printing Notebooks to PDF or HTML files is not always optimal and can be very difficult to "clean up".
- Notebook scripting encourages "worst practices" Python development as custom packages are not as easily imported.
- Notebooks run with a single "kernel" (Python Interpreter) instance that requires a manual restart, otherwise it will remain persistent. This also means that all memory and aliasing will be persistent for the runtime of the "kernel", which can quickly lead to silent or overtly-confusing bugs.
- Any code written in a Notebook needs to be copied out of the rendered view and pasted into a proper Python module if you want to productionalise the code, since you cannot import code from a Jupyter Notebook (remember that the Notebook is a JSON file and not Python code).


Yes, this is an argument against Jupyter Notebooks by providing a repository of Jupyter Notebooks.

![Thanks, I Hate It](./imgs/Thanks-IHateIt.gif)

People say things like "don't touch that, it's hot!", but people still touch it, and people still get burned. And sometimes, people demand that you hand them burning hot coals and they assure you "No, no, it's fine, I got this!", and you don't wanna do it, but they're the people who've hired you to rake and heat-up the coals, so if you wanna keep gettin' paid, you gotta keep heatin' up the coals.

![Seinfeld, "I will never understand people."](./imgs/Seinfeld-Elaine-NeverUnderstandPeople.gif)

You can't make people make good choices. So yeah, this a repository of Jupyter Notebooks that's also an argument __against__ ever using Jupyter Notebooks. So let's just consider this to be oven mitts for handling the coals. In a perfect world, you wouldn't be handling hot coals for no reason, and thus you wouldn't need oven mitts. But it is what it is.

![The Irishman, "It is what it is."](./imgs/TheIrishman-Pesci-ItIsWhatItIs.gif)


### Argument: The Combined View isn't _that_ Useful

Often people may argue that the blend of code, graphs, images, and Markdown (README-like) sections can make for a comprehensive tutorial that allows for running, reading, and presenting code all in one file -- which is basically true. We agree, it's a convenient way to view code, especially as a tutorial, to just scroll through an interactive Notebook.

However, we argue that it's a presentation tutorial, not a "best practices" tutorial.

Except in specialised circumstances, does a tutorial really need to be interactive? What is the interactivity of the Python Notebook actually providing to the reader?

Yes, they can edit the code in each cell and re-run them, or they could add their own cells and modify the notebook by rerunning the whole thing with their embedded changes. But how many tutorials really benefit from that one-off approach? If you're teaching a concept that's implemented in code, the Notebook sits in a strange middle-ground between proper-software and psuedo-code.

Arguably, the benefit of a Notebook is for the laziness of the author. The author can blend code, graphics, and Markdown explanations (README blocks) all into a single file, written in a single editor, and developed in a single sitting. There's no back and forth, there's no multiple files or multiple modules, and it's all right there, rendered "live". It doesn't benefit the audience, because they need to install the `jupyter` Python package and run a Jupyter "kernel" to get the `.ipynb` JSON file to render into the Notebook format that the author was looking at. It's an undue burden on the audience because its not innately readable in any ubiquitous Web-browser or PDF viewer applications.

Now, to concede a bit, GitHub does (as of recently) generate an HTML view of a Jupyter (iPython) Notebook. So if you commit it to GitHub, you can view the file and see it rendered. However, this can fail for relatively "small" Notebooks of `5 MB` or larger. Also, the embedded SVG rendering in the GitHub view has issues. Also, this requires providing a GitHub link to a specific file on a specific branch in a repository, and depending on the URL it may even be limited to a specific commit. That's not really useful to share around because any updates will end up at other URLs. And, again, you're asking your audience to be comfortable navigating GitHub and being aware of the Git tree-structure enough that they can figure out if they're looking at the latest version or not.

Could an HTML or LaTeX-based PDF with Code Listings (code blocks) and embedded graphics actually be better? Wouldn't it be more accurate to provide a repository of valid, well written code modules and packages, and then accompany that with a PDF or HTML document that goes through your discussion and provides snippets of the actual code?

Modules and Packages that are properly written can also have unit-tests, functional tests, integration tests, and data integrity tests. You can have logging, you can have imports, you can split-up the code into packages and sub-packages that could be portable and reusable, and the code itself could have extensive, reliable documentation.

A storytelling "notebook", should be an accompaniment to clean, well-organised, well-documented, compartmentalised code. It shouldn't replace it. You've done yourself a disservice, you've done your audience a disservice, and you've ended up with an esoteric JSON file that's a mess of Markdown and Python code all jammed into HTML-escaped JSON strings. You can't hand someone an `.ipynb` file and they can just read it, they need to spin-up a `jupyter` instance and open it themselves.

And even if you try printing to PDF or exporting as a standalone HTML file, is everything going to be rendered just how you saw it? You've also now lost all the interactivity. Does it render in mobile browsers and viewers? Is the PDF a bit of a mess with all the extra HTML styling not really aligning with the PDF page breaks? You maybe intended it to appear as a document, but it could print out with cut-off texts or misplaced graphics and all look pretty unprofessional.

Didn't you write this Notebook to try and provide something simpler and easier to follow for people who aren't _that_ familiar with Python code? Isn't it written for their benefit?

Or was it just kinda slightly more convenient for you ... even though it needs a special runtime, doesn't really work with most text-editors or IDEs, and requires you to write all your code in basically a single stream-of-consciousness explicit mess of script statements without the benefits of custom classes or functions?

![Star Trek: The Next Generation, "I hate this!"](./imgs/StarTrek-NextGeneration-Data-HateThis.gif)


### Argument: The Runtime Kernel is a Death Trap

Developing with a Notebook requires a "kernel" to be running, which is a single instance of a Python interpreter. The Jupyter (iPython) application basically runs a local webserver and a CGI which deals with the JSON-to-HTML and HTML-to-JSON back and forth of the editor view. Anytime you "run" a cell in a Notebook, that JSON code is parsed in Jupyter (iPython) into a chunk of Python code and dumped into the (still) running Interpreter.

This process is sequential but discontinuous. You're not running all your code, you're only a single cell at a time, and there's nothing stopping you from running the cells out of order.

This also all means that every executed cell's code is sitting in the same memory space, for the same interpreter runtime, as long as the "kernel" is running.

Due to Python's aliasing and shallow-copy memory-management, this means you can easily walk yourself into a circle of broken aliases, requiring that you restart the "kernel" if things stop working.

_And worse!_, this means that you can also get silent failures (bugs) in your code due to implicit aliasing; where you won't be able to see these errors unless the effects are obvious.

For Data Science, Statistics, Mathematics, Engineering, and Machine Learning, this is a little more than just ___"kind of"___ a worst-case-scenario.

If your code isn't doing what you think its doing, especially if you're seeing your results for the first time and have no means of gauging correctness, you could end up with totally wrong expectations, results, or interpretations.

Imagine a realistic scenario of spending hours tweaking a Machine Learning model in a cell in a Notebook, and finally getting things working, embedding an intuitive understanding of the design in your mind. Then the next day you restart the Jupyter "kernel" and run through all the cells in order to get back to what you were doing, and now everything is broken!? What happened!?

Well, if you reused an alias and had run certain cells out of order, you could've spent hours optimising a model based on your raw, untransformed data instead of your feature-ready transformed-data. Since this was your first time tweaking and optimising your model, and since you don't have all the data memorised, there was no way for you to know until you shutdown everything, re-ran it all, and came out with a totally different result!

Now imagine that that process has some kind of embedded stochastic aspect to it, such that every time you run through the algorithm it's just a little bit different. How can you tell the difference between a bug and the naturally random nature?

Does your notebook have unit tests? functional tests? implementation tests? Can your algorithm be run on dummy data or does it only work for "real" data?

How diligent are you with your aliases? How diligent are you with your shallow-copies and pass-by-object-reference memory management?

Does this seem familiar?

```python
b = [3,] * 3;
# [3, 3, 3]

a = [b,] * 2;
# [ [3, 3, 3], [3, 3, 3] ]

b[1] = 2;
# [3, 2, 3]

print(a);
# [ [3, 2, 3], [3, 2, 3] ]
```

Yikes! What happened?!?

`b` is a `list` Class instance that's created using the `*` operator by copying the original list contents 3 times. As shown, `b = [3, 3, 3]`, a list of length 3, with indices `0`, `1`, and `2`, and the contents are all the value `3`. _Then_, we create `a` in the same manner, but instead of being created from primitive integers, `a` is created as a list of duplicates of the object `b`, which is itself a list, as we just said.

So now, `a` is a list of two instances of `b`. But did you realise that they would be shallow copies? `a` is really a list of 2 references, and each reference points to the same thing, `b`. And it's not even actually `b`, the alias, it's whatever memory `b` the alias was pointing to at the time of the creation of `a`.

But, so long as `b`, as an alias, isn't reassigned to new memory, then anything that we do to `b` that modifies the underlying memory will modify the contents of `a`. Usually, this means that any methods using the `.` (dot) operator on `b` will be the ones that modify the underlying memory. But, there are a lot of other syntaxes that actually are just shorthand for self-modifying methods, like the combination of the square-brackets (`[]`) and the assignment (`=`) operators. The square-brackets return a reference to the underlying contents of `b`, and the assignment operator modifies the value at that reference.

So when we call `b[1] = 2`, we're saying the 2nd (zero-indexing) element in the list that's pointed to by the alias `b` should be changed to the integer value `2`, that means that anything else pointing to that same list in memory is now being modified as well. Since `a` is just shallow-copy references to that list that was aliased as `b`, the last line shows that without ever touching `a`, we've modified it by modifying `b`.

Yikes!?

The above is a really simple example. Do you know what all your `pandas` and `numpy` methods are doing? Are they shallow or deep? Are they pass-by-object-reference or pass-by-copy? Are you reusing aliases? Are you using temporary/dummy aliases? Are you iterating with shorthand? Are you dereferencing?

Has the terseness of a Jupyter (iPython) Notebook encouraged you to aim for brevity over explicit accuracy?

Imagine the above code isn't so sequential but is now split across cells that when run in a certain order can create the same outcome, by having later code called before earlier code and accidentally re-alias on itself. Now imagine that that happend 5 hours ago and you haven't restarted the "kernel" and you're deep in the weeds of debugging or tweaking your mathematical model or some kind of Machine Learning algorithm, trying to tweak the parameters and configuration until the output looks how you expect it to look.

The computer's gonna let you do whatever you wanna do and it's only gonna do what you told it. But if you didn't know what you told it, or you accidentally said some things out of order, nothing's gonna stop you from continuing along that path, unaware of the consequences until you (hopefully) decide to shutdown and run everything (in order) from scratch.

In normal Python development, when you call `python -m my_pkg.my_module` or `python ./my_module.py` you're calling the interpreter once. If it errors out or fails, it stops. If it succeeds, it stops. When you call your code again, the interpreter runs again. `python` is the interpreter, that's the "kernel", and it only ever runs once.

If you get an error in a Jupyter Notebook, it'll tell you, but it might __not__ stop the "kernel". You can actually "correct" errors without restarting the "kernel", depending on how bad the error is or not. But then what about all those aliases? Are they gone? Did you overwrite them?

What if you wrote your code and created 10 new aliases, but it fails and the "kernel" keeps running, so now 9 of the 10 aliases are in memory, but the 10th one failed so it didn't get created. Now you go back, look at your code, find the bug, and rewrite that cell, but this time you only need 4 aliases. The 10th one never got created, but you have 5 aliases that were created that you now deleted from your Notebook. Are they gone? Nope! There's a pretty good chance they're just sitting there in the "kernel", and you can still reference them, even though they're not declared anywhere in your current code.

__When you have a persistent "kernel", deleting code is not the same as deleting aliased memory!__ -- Yikes again!!?!

So, wait, doesn't this all mean that the convenience of a Notebook relies on your extreme diligence in software development best-practices with optimally proper Python?! And isn't that kind of antithetical to convenience, out of order code, a single persistent dumpster-style runtime, and a single monolithic module???

So what, again, is the benefit of a Notebook?!

![Star Trek: The Next Generation, "I hate this!"](./imgs/StarTrek-NextGeneration-Data-HateThis.gif)

### In Summary: Don't Do It

Just to summarise: don't use Jupyter (iPython) Notebooks ... unless someone forces you to.

Even then, try and convince them that it's not gonna be helpful. Yeah, maybe it's slightly faster to "whip up a prototype", but really you're creating twice as much work because now you have to rewrite the notebook into Python modules to actually be able to use it in any kind of production environment. And there's no guarantee that something that worked in your Notebook will work in production, because it's all out of context!

Ok, ok, we'll concede slightly again, that, yes, there are things like AWS [SageMaker Notebooks](https://aws.amazon.com/sagemaker/) and GCP [AI Platform Notebooks](https://cloud.google.com/ai-platform-notebooks) that use Python notebooks and allow you to run production-like Data Science R&D ... but do they really?

Is your DevOps team or Backend Engineering Team really _actually_ excited about figuring out how to integrate these notebooks into the production workflow? How often are you running these notebooks? How clean is the code? How well tested? Are there unit-tests? functional tests? integration tests? Do they have to read-in all the data every time they run? How costly are they to run? How much are the data input/output costs? How fast do they run? Can you optimise them? Are you reusing code that's used elsewhere in production or have you copy-pasted code from production repos? How many new bugs have you created? How many old bugs are left unresolved? How do you sleep at night?!

Would you really, actually, truly consider this "productionalised"?

Just don't do it. That's our advice. Feel free to ignore us, of course. We're just one person, and people usually don't listen to us anyways.

![Seinfeld, "I don't like this thing!"](./imgs/Seinfeld-Elaine-IDontLikeThisThing.gif)
