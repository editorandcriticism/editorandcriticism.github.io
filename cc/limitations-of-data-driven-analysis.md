---
title: The Limitations of Big Data and Data-Driven Decision Making
---


# The Limitations of Big Data and Data-Driven Decision Making

As a vague metaphor, the so-called data lake comes with a certain mythology attached to it, like Lock Ness shrouded in fog. The monster in the lake is, of course, big data, and misconceptions about data  steep the lake in mythology. The dominant myth is "the widespread belief that large data sets offer a higher form of intelligence and knowledge that can generate insights that were previously impossible, with the aura of truth, objectivity, and accuracy," as danah boyd and Kate Crawford put it.[^danah] Data, however big it may be, has its limits.

[^danah]: danah boyd & Kate Crawford (2012) Critical Questions
for Big Data, Information, Communication & Society, 15:5, 662-679, DOI:
10.1080/1369118X.2012.678878. The essay is available at http://dx.doi.org/10.1080/1369118X.2012.678878

The authors of _Doing Data Science_, for instance, cite the subjectivity of data: "Data represents the traces of the real-world processes, and exactly which traces we gather are decided by our data collection or sampling method. You, the data scientist, the observer, are turning the world into data, and this is an utterly subjective, not objective, process. After separating the process from the data collection, we can see clearly that there are two sources of randomness and uncertainty. Namely, the randomness and uncertainty underlying the process itself, and the uncertainty associated with your underlying data collection methods."[^doingds]

[^doingds]: _Doing Data Science_, Rachel Schutt and Cathy O’Neil, O’Reilly, 2014, p. 19. 

In interpreting the results of a data analysis, group think can undermine clarity. People tend to be uncritically influenced by the system or culture in which they are embedded. Collaboration, though heralded as an unquestioned good, can lead an organization astray because it is [all too easy to project the import of an interpretation into the data itself](https://www.criticism.com/da/da_indet.html)---and that is the locus of error. As Schutt and O'Neil put it in _Doing Data Science_, "Another way in which the assumption that N=ALL can matter is that it often gets translated into the idea that data is objective. It is wrong to believe either that data is objective or that 'data speaks,' and beware of people who say otherwise."[^p25]

[^p25]: _Doing Data Science_, p. 25.

Even published research findings are often false, or turn out to be false when more evidence surfaces. In 2005, John P. A. Ioannidis, now a professor of health research and policy at Stanford University School of Medicine, published a paper maintaining that most published research findings are false. The paper, which is the most-accessed article in the history of the Public Library of Science, summarizes all the things that frequently go wrong with a study. "Simulations show that for most study designs and settings, it is more likely for a research claim to be false than true. Moreover, for many current scientific fields, claimed research findings may often be simply accurate measures of the prevailing bias."[^wrong] 

[^wrong]: Ioannidis JPA (2005) Why most published research findings are false. PLoS Med 2(8): e124. 

Ioannidis's paper underscores the importance of using data rigourously,[^rig] critically,[^crit] and ethically.[^ethic] Without critically understanding and interpreting data, the results are likely to lead an organization to make the wrong decisions, and in this new world that can be costly. 

[^rig]: See, for instance, _Mining of Massive Datasets_ by Anand Rajaraman and Jeffrey David Ullman, Cambridge University Press, 2011. The book focuses on practical algorithms that have been used to solve key problems in data mining and which can be applied to the largest datasets. 

[^crit]: For an entertaining book-length example of how to examine data critically, see _Why Zebras Don't Get Ulcers_, Third Edition, by Robert M. Sapolsky, Holt Paperbacks, 2004.

[^ethic]: See Susan Etlinger's 2014 Ted Talk titled "What do we do with all this big data?" at http://www.ted.com/talks/susan_etlinger_what_do_we_do_with_all_this_big_data?language=en. In the talk, Etlinger makes the connection between understanding data and using it ethically. 

Even more important, though, is acknowledging the limitations of big data. "Big Data can be especially helpful in systems that are consistent over time, with straightforward and well-characterized properties, little unpredictable variation, and relatively little underlying complexity. But not every problem fits those criteria; unpredictability, complexity, and abrupt shifts over time can lead even the largest data astray. Big Data is a powerful tool for inferring correlations, not a magic wand for inferring causality."[^yorker] 

[^yorker]: http://www.newyorker.com/tech/elements/steamrolled-by-big-data

The interpretation of data can also be exceedingly subtle. On the surface, the data may appear to indicate one thing, but it might in fact actually show something else entirely---a point that's been repeatedly demonstrated during the scholarly give-and-take over social science research. But sometimes, in industry, where critical perspectives are often overwhelmed by group think oriented toward the current bias, more subtle but accurate interpretations of the data can be lost. With rigorous data collection, the data might contain events, but it does not contain either the motivation for or the outcome of those events. Correlation is not causation. Description is not explanation.  

The analysis of soccer players during games provides an example. "Modern football data analysis has its origins in a video-based system that used computer vision algorithms to automatically track players. Developed 20 years ago in France, as a tool for broadcasters, it was adapted as a coaching aid and first used at Derby County in 1998 by Leeds-based company Prozone. This and other video tracking systems use multiple cameras inside stadiums, and human operators who manually record data, to gather information on things such as possession, passes, tackles, runs, interceptions and shots."[^soc] And a data repository is, no doubt, a useful place to store such video footage, along with other data about players, games, and so forth. 

[^soc]: How science is fine-tuning our elite footballers, by Nic Fleming, The Guardian, Sunday 2 August 2015, 
http://www.theguardian.com/football/2015/aug/02/science-fine-tuning-elite-footballers.

“Until recently, it was very much about collecting data on what had happened, without looking at why it had happened,” says Paul Power, a data scientist at Prozone. Power cites the great Italian defender Paolo Maldini as an example of a player who might be marked down by a system that values tackling and intercepting; because his positional play was so good he had less need to do these things."

But data scientists evaluating soccer are now advancing a more sophisticated approach. “We’re reconceptualising football as a complex dynamic system, using complex systems theory, which is derived from chaos theory,” Power told the Guardian. "The idea is to capture more useful information about, for instance, inter-player co-ordination, players making themselves available for passes and the ability of players to block the passing options of opponents through positional play."

A domain in which the hype of big data is colliding with the cold reality of traditional research methods is medicine. "In the lab, ensuring that the data-mining conclusions hold water can also be tricky. By definition, a medical-records database contains information only on sick people who sought help, so it is inherently incomplete. Also, they lack the controls of a clinical study and are full of other confounding factors that might trip up unwary researchers. Daniel Rubin, a professor of bioinformatics at Stanford, also warns that _there have been no studies of data-driven medicine to determine whether it leads to positive outcomes more often than not._ Because historical evidence is of “inferior quality,” he says, it has the potential to lead care astray." 

[^clinical]: Can Big Data Tell Us What Clinical Trials Don’t?, Oct. 3, 2014, _The New York Times_, by Veronique Greenwood, at http://www.nytimes.com/2014/10/05/magazine/can-big-data-tell-us-what-clinical-trials-dont.html. 

"In fact, one could see the entire field of artificial intelligence as an inadvertent referendum on Big Data, because nowadays virtually every problem that has ever been addressed in A.I.—from machine vision to natural language understanding—has also been attacked from a data perspective. Yet most of those problems are unsolved, Big Data or no."[^yorker2]

[^yorker2]: http://www.newyorker.com/tech/elements/steamrolled-by-big-data

But what does this all have to do with large data repositories? It helps demonstrate what a data repository can and cannot do. There are limitations to the data, the analytics, and the analysts. 

It also exposes two things: First, be especially wary of vendors who tout the data-tells-all story and who seek to replace analysts with analytics. Second, make cultural and technical shifts, including hiring academically trained data scientists, to adapt your organization to the era of big data.

## Evaluating Analytics Products

Understanding the limitations of big data can help you evaluate analytics products. Just as you should approach your data and your interpretation of it with a sceptical, critical eye, so to should you look at analytics products and their representatives. Be aware of anybody who makes claims about just focusing on the data or spouts hyperbole about the data telling its own story or the day being always right. You should also be wary of those who claim you can analyze streaming data so quickly that you do not need to store the results. 

"As one skeptical industry insider, Anthony Nyström, of the Web software company Intridea, put it to me, selling Big Data is a great gig for charlatans, because they never have to admit to being wrong. 'If their system fails to provide predictive insight, it’s not their models, it’s an issue with your data.' You didn’t have enough data, there was too much noise, you measured the wrong things. The list of excuses can be long."[^yorker3]

[^yorker3]: http://www.newyorker.com/tech/elements/steamrolled-by-big-data

Indeed, all sorts of things can go wrong in an analysis of a data set, as Rachel Schutt and Cathy O’Neil demonstrate in their book, _Doing Data Science_. There is much more subjectivity in the process than most people think, even with regard to seemingly straight-forward data from sensors and instruments. The point is to trust neither your data nor your interpretation of it. If you understand the limitations of big data and adopt a critical perspective to analyzing data, it puts you in a better position to evaluate vendor offerings. For a primer on data science, see Schutt and O'Neil's book, _Doing Data Science_, published by O'Reilly.    


## Open Access to Data for Analytics, Interpretation, and Collaboration

Two aspects of a data science program can counter misinterpretations and subsequent misguided decisions that go hand in hand with the use of data to drive business decisions: 

1. A culture of questioning. Institute a culture that values questioning. Everyone in the organization should be able to openly question the interpretation of a dataset and the decisions that follow, including those of executives. Flattening the hierarchy of an organization not only makes it more agile, but also helps institute a critical culture. Hierarchy also promotes the notion that the highest-paid person knows best, despite someone else's interpretations of the data that might indicate otherwise. 

1. Open, transparent access to data. Within the constraints of information security and compliance regulations, give everyone in the organization access to the data platform and the information it contains so that anyone can query it, analyze it, and interpret it. 

Although one of these imperatives is cultural, the other is technical: Open access to everyone within the enterprise to the extent that security policies or techniques, such as masking, allow. 



