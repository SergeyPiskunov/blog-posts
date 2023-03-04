# Model Thinking course from the software engineer’s perspective

I want to give a review on the "Model Thinking" course, which I have recently completed using Coursera platform. 
Although this 8-week online course from Michigan University aims to make us better citizens of the world and decision-makers 
in general, I will share my thoughts about how that course's material may be applied to software engineering. 
I'm going to  discuss several course sections that were the most relevant for me.

## Why do we model?

As the first quote from this course's material, I'd like to put this one: *"Models are the new Lingua Franca which allow 
people from different domains to communicate their ideas simply and clearly."*. We all know from Domain Driven Design 
how crucial for a software project is to have a ubiquitous language between engineers and non-technical colleagues. 
Enriching our documentation with models makes communication between team members even more effective.

*"We don't want to let the models tell us what to do. We want the models to help us make better choices. Smart people use 
both models and experience and not just blindly use models.".* Models are not a silver bullet, though; we should understand 
their applications and restrictions, making them just yet another tool but not a replacement for common sense and experience.

One of the most widespread examples of using models in a software engineer's routine is explaining the complexity of algorithms. 
We usually do not say "The Bubble Sort" is slow, but the "Merge Sort" is faster because each person has their own understanding 
of fast and slow. We say the "Bubble Sort" has O(n^2) time complexity, and the "Merge Sort" has the O(n log n). So during 
decision-making, we operate not with our emotions and feelings about the speed of algorithms, but we use their 
mathematical models. That gives us a fair performance comparison and understanding of possible applications of those algorithms.

## Sorting and peer effects.

Here we can find an exciting model of social behavior, which may explain, for example, how we adopt new technologies within 
the industry (or new ideas within a team). *"Granovetter's Model - The tail wags the dog. The people at the tail of the normal 
distribution are extremists, who sometimes drive what happens because of the chain reaction of thresholds of other people. 
Collective action is more likely if there are lower thresholds (the "tail" which leads to a cascade effect of "wagging the dog") 
and there is more variation in thresholds (which increases the probability of the chain reaction)."*.

Standing Ovation Model - Granovetter's model, in which the cascade effect is amplified by "expert" opinion, the opinion 
of a friend, a celebrity, or other influencers.

## Aggregation.

This section explains a lot of concepts, which a regular software developer may face in a day-to-day work, like the Bell Curve, 
Standard Deviation, and Mean. We may often see those terms in performance-testing reports or monitoring dashboards.

## Decision models.

I have found this section useful as it gives us decision-making tools to deal with complex subjects with multiple 
characteristics - "Multi-Criterion Choice Models". Imagine you must choose a framework or library among a dozen options. 
While each candidate has a dozen of aspects. A comparison table may be the right tool for that, but you may need to learn 
how to make the results of such comparison even more expressive using weights and distances. Also, one of the essential 
things in this section is a general recap on the Probabilistic Theory, Decision Trees — a crucial grounding for every engineer.

## Models of people. Thinking Electrons.

This section may not give us concrete technical advice, but it sheds light on how people behave. The authors show examples 
of people's rational, irrational, and rule-based actions and different types of biases. That may help us to understand 
people better and thus to be better team players.

## Linear models.

The Linear Models section gives us many insights not only about reading the output of some types of statistical 
analysis (for example, Regression Output), but about ways to explain the raw data you have. For example, you may find 
that the more execution threads do you add, the fastest your code becomes. You may assume that the speed of your code 
linearly depends on the amount of resources you have, and you may plan your server's capacities according to that assumption. 
But one of the crucial caveats here is to be careful about extrapolating your linear data outside the data range. 
At some point, you may notice that adding more X does not give you more Y.

*"Correlation is not causation"* is also important to remember during any historical data analysis and attempts to 
predict the future using that data. The authors give you a wise idea that to optimize your system even more, you might 
need a so-called "New Reality". To have better results, you are just building the new system instead of optimizing an old one. 
"The New Reality - is moving outside the box, explained by linear models and coefficients to the new system. 
Instead of endless optimizing of the SQL queries, try to re-align your data so that it may fit into the NoSQL paradigm."

## Economic growth.

What kind of economic-related knowledge may we reuse in our software engineering paths? Our engineering paths consist 
not only of technologies we know now but of how we evolve as professionals and grow. That growth has much more in common 
with economic growth than you may think. Assuming that our skill set is a kind of our personal GDP, we may apply the 
economic growth models to ourselves! The basic economic growth model suggests that Sustainable growth requires innovation. 
Let me quote the excerpt: *"You can't just do more. At some point, the rate at which things fall off and the rate at which 
things increase is just going to even out. If you look at the data on what makes for really successful people, people 
who are very successful in their careers continue to learn."*. That is especially important in the age of replacing some 
jobs with Machine Learning systems and other types of automation.

*"Growth requires creative destruction".* Another example is the evolution of programming languages. I'm not going to 
start the Holy War related to the specific languages, but I want to say, that there is a mathematical model, showing us that, 
at some point, it is better to create (or adopt) the new fancy programming language instead of cluttering a 20-year-old one 
with new concepts, while also trying not to break backward compatibility and its idiomatic style.

## Diversity and innovation.

This section describes a thing we face almost every day at our work. The "No Free Lunch Theorem". I could not find words 
better than the author's explanation - *"No Free Lunch Theorem tells us that no single heuristic is always effective. 
A heuristic that works great for one problem class may be ineffective for another problem type... All algorithms that 
search the same number of points with the goal of locating the maximum value of a function defined on a finite set perform 
exactly the same when averaged over all possible functions.*" That may come in handy during the design and optimization of 
algorithms/business logic. This section has some additional problem-solving tips as well - *"When we go about solving problems, 
the first thing we do is we encode them. We have some representation of the problem. That representation determines how 
hard the problem will be."*. That is why it is not a good idea to start writing code immediately after reading the task description. 
It's better to invest decent time in design and preparation, pseudo-coding, and leave the coding itself as the less 
important routine stage. We may find in this section a mathematical proof of why teams are better at problem-solving 
than individuals - because of diversity, perspectives, heuristics, and recombination of those new ideas. You'll always 
uphold a command work after hearing that explanation.

## Networks.

This is again something one may have studied in college, but worth repeating. Networks and graphs are literally everywhere, 
from the computer network itself and distributed systems within those networks to the object inheritance and dependency 
graphs in the source code. The McCabe code complexity analysis, graph databases, and graph query languages are also based on 
the theory explained in this section.

## Conclusion.

I have reviewed a little more than half of the sections of the "Model Thinking" course—only those I have found the most 
applicable to my personal path of a software engineer. However, your list of favorite concepts may differ because the 
knowledge you'll get after taking this course is rather a meta-knowledge that may be applicable to a wide variety of 
cases in your life. So, I encourage not only software engineers, but all to take that course.

## Links

[Coursera "Model Thinking" course](https://www.coursera.org/learn/model-thinking)
