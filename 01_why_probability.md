## Chapter 1
## Probability
The following excerpt is taken from Prof. M.A Canela's lecture notes.

    1.1. Why probability?

    When researchers perform statistical analyses, they wish to draw conclusions which apply, not only to the sample on which the data have been collected, but to a population from which the sample has been extracted. This is called inference. For instance, market researchers want to draw conclusions applying to the population of all potential customers, though the data are collected on a sample of actual customers. Note that the term population is used here in the statistical sense. So, it applies to commercial transactions, companies, prices, etc.

    The results of a statistical analysis cannot be trusted completely, since they are derived from partial information. So, they are reported with an indication of the extent to which we can trust them. The probability language allows us to manage this. The probability definitions are various, some of them in the philosophical realm. In this course, we are not interested in the conceptual aspects, but in the rules. Why? Because there are certain standards that your conclusions need to satisfy, if you want your paper to be published, or your PhD dissertation admitted. One of them is that you report significant results. What does this mean? Roughly speaking, that you should be at least 95% sure of your conclusions. In technical terms, that the probability of results such as those you have obtained would be less than 0.05 if your conclusions were not valid. Thus, it is enough for you to have an idea of the probability of an event as a numerical measure of how likely it is to happen, and to know the rules for operating with probability values.

    There have been many attempts to define the probability in a consistent way. Some of them are based on
    philosophical or psychological ideas about how humans deal with uncertainty, like subjective probabil-
    ity. We leave these apart (not meaning that they are not interesting), focusing on a sound mathematical approach. There are two main perspectives of probability:

    - In the **frequentist** approach, the probability of an event is seen as the limit of its proportion of occurrence, as the number of observations increases. For instance, when saying that the probability
    of a newborn being male is the 52% (a realistic figure), we understand that, out of a big number
    of births, approximately 52% of them will produce a male. Thus, in the frequentist approach,
    probabilities are understood as related to large numbers.

    - Under a different perspective, a probability is seen as a numerical measure of our expectations
    about the occurrence of an event. Then, a probability is related to certain information. With
    new information, the probability changes. This is the point of view of **Bayesian** statistics. The
    Bayesian scientist attributes a probability to an event before collecting data, the prior probability. After collecting data, the probability is recalculated, leading to a posterior probability. For instance, a student of medicine reads that the probability of a male newborn is 52%. Later, he/she becomes a gynecologist and goes to a hospital, starting his/her career with a series of
    ten consecutive female births. The prior probability of 52% can then be updated to a posterior
    (lower) probability. Here, the probability is just an assessment relying on information. The incoming information does not change the (unknown) proportion of male children, but changes our
    assessment.

    You shouldn't care about this for the moment being. You will take the probability of an event as an
    "ideal" proportion, meaning that the greater the number of observations, the closer you are to such
    ideal. What matters is the set of rules that the assignment of probabilities to events must satisfy...

## References
1. Professor Miguel-Angel Canela Lecture Notes: Probability & Statistics, Department of Managerial Decision Sciences, IESE Business School 

2. MH DeGroot & MJ Schervish (2002), Probability and Statistics, Addison-Wesley.