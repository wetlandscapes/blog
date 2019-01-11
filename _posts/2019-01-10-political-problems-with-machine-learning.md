---
title: "Political problems with machine learning in the context of water justice"
author: "Jason Mercer"
---



This morning I was listening to a podcast from Marketplace from a couple of days ago and heard an interesting piece on using machine learning to identify where lead pipes might be located in the beleaguered Flint, MI. [Alexis Madrigal](https://www.theatlantic.com/author/alexis-madrigal/) provided a follow-up in the Atlantic to a proceeding paper in which the original authors described a technique for identifying, with 80 % accuracy, lead pipe locations in Flint using different "machine learning" techniques -- specifically, a form of logistic regression (logistic lasso), random forests, and XGBoost. I'd not heard of XGBoost before, but apparently it is included in the `caret` package for R, as well as in a number of other languages.

However, despite the relatively high accuracy of the authors' results, the method was abandoned when an environmental engineering consultancy took over the contract for finding lead pipes. Bowing to political pressure, and an apparent lack of clarity as to how the machine methods actually worked, the new accuracy rate for finding houses with lead is closer to 15 %! I'm not sure if this concept applies, but from a binary perspective, that is worse than just guessing which houses have lead, which one would expect to be closer to 50 %.

In any case, I thought this issue was an interesting example of:

1. Using machine learning to solve a practical problem related to environmental/water justice.
2. The problem of using machine learning in the context of a social/political structure that may not trust the results of an algorithm that users do not inherently understand.

In other words, I think this highlights the kind of challenge that folks in the data science world face, in terms of using their work for bettering society -- we need to get better at explaining, in simple terms, how a particular method works (or doesn't) so that we develop trust with users. Its certainly not an easy job, but in some cases (like in Flint) it could literally improve, or even save, lives.

For more on the issues:

* [Marketplace piece](https://www.marketplace.org/shows/marketplace/01082019) (story starts at 16:51)

* [Atlantic article](https://www.theatlantic.com/technology/archive/2019/01/how-machine-learning-found-flints-lead-pipes/578692/)

* Proceedings paper: [published](https://dl.acm.org/citation.cfm?id=3219896) or [pre-print](https://arxiv.org/pdf/1806.10692.pdf)
