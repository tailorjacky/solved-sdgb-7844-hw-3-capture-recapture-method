Download Link: https://assignmentchef.com/product/solved-sdgb-7844-hw-3-capture-recapture-method
<br>
Submit two files through Blackboard: (a) .Rmd R Markdown file with answers and code and (b) Word document of knitted R Markdown file. Your file should be named as follows: “HW3-[Full Name]-[Class Time]” and include those details in the body of your file.

Please submit your solutions only once! Complete your work individually and comment your code for full credit. For an example of how to format your homework see the files related to the Lecture 1 Exercises and the RMarkdown examples on Blackboard. <strong>Show all of your code in the knitted Word document.</strong>

In the beginning of the 17th century, John Graunt wanted to determine the effect of the plague on the population of England; two hundred years later, Pierre-Simon Laplace wanted to estimate the population of France. Both Graunt and Laplace implemented what is now called the <em>capture-recapture method. </em>This technique is used to not only count human populations (such as the homeless) but also animals in the wild.

In its simplest form, <em>n</em><sub>1 </sub>individuals are “captured,” “tagged”, and released. A while later, <em>n</em><sub>2 </sub>individuals are “captured” and the number of “tagged” individuals, <em>m</em><sub>2</sub>, is counted. If <em>N </em>is the true total population size, we can estimate it with <em>N</em><sup>ˆ</sup><em><sub>LP </sub></em>as follows:

(1)

using the relation. This is called the Lincoln-Peterson estimator<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>.

We make several strong assumptions when we use this method: (a) each individual is independently captured, (b) each individual is equally likely to be captured, (c) there are no births, deaths, immigration, or emigration of individuals (i.e., a closed population), and (d) the tags do not wear off (if it is a physical mark) and no tag goes unnoticed by a researcher.

<u>Goal: </u>In this assignment, you will develop a Monte-Carlo simulation of the capture-recapture method and investigate the statistical properties of the Lincoln-Peterson and Chapman es-

1

timators of population size, <em>N</em>. (Since you are simulating your own data, you know the true value of the population size <em>N </em>allowing you to study how well these estimators work.)

Note: It is helpful to save your R workspace to an “.RData” file so that you don’t have to keep running all of your code every time you work on this assignment. See Lecture 8 for more details.

<ol>

 <li>Simulate the capture-recapture method for a population of size <em>N </em>= 5<em>,</em>000 when <em>n</em><sub>1 </sub>= 100 and <em>n</em><sub>2 </sub>= 100 using the sample() function (we assume that each individual is equally likely to be “captured”). Determine <em>m</em><sub>2 </sub>and calculate <em>N</em><sup>ˆ</sup><em><sub>LP </sub></em>using Eq.1. (Hint: think of everyone in your population as having an assigned number from 1 to 5,000, then when you sample from this population, you say you selected person 5, person 8, etc., for example.)</li>

 <li>Write a <u>function </u>to simulate the capture-recapture procedure using the inputs: <em>N</em>, <em>n</em><sub>1</sub>, <em>n</em><sub>2</sub>, and the number of simulation runs. The function should output in list form (a) a data frame with two columns: the values of <em>m</em><sub>2 </sub>and <em>N</em><sup>ˆ</sup><em><sub>LP </sub></em>for each iteration and (b) <em>N</em>. Run your simulation for 1,000 iterations for a population of size <em>N </em>=5,000 where <em>n</em><sub>1 </sub>= <em>n</em><sub>2 </sub>= 100 and make a histogram of the resulting <em>N</em><sup>ˆ</sup><em><sub>LP </sub></em>vector<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>. Indicate <em>N </em>on your plot.</li>

 <li>What percent of the estimated population values in question 2 were infinite? Why can this occur?</li>

 <li>An alternative to the Lincoln-Peterson estimator is the Chapman estimator:</li>

</ol>

(2)

Use the saved <em>m</em><sub>2 </sub>values from question 2 to compute the corresponding Chapman estimates for each iteration of your simulation. Construct a histogram of the resulting <em>N</em><sup>ˆ</sup><em><sub>C </sub></em>estimates, indicating <em>N </em>on your plot.

<ol start="5">

 <li>An estimator is considered <em>unbiased </em>if, on average, the estimator equals the true population value. For example, the sample mean is unbiased because on average the sample mean <em>x </em>equals the population mean <em>µ </em>(i.e., the sampling distribution is centered around <em>µ</em>). This is a desirable property for an estimator to have because it means our estimator is not systematically wrong. To show that an estimator <em>θ</em><sup>ˆ </sup>is</li>

</ol>

an unbiased estimate of the true value <em>θ</em>, we would need to mathematically prove that E[<em>θ</em><sup>ˆ</sup>] − <em>θ </em>= 0 where E[·] is the expectation (i.e., theoretical average)<a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a>. Instead, we will investigate this property empirically by replacing the theoretical average E[<em>θ</em><sup>ˆ</sup>] with the sample average of the <em>θ</em><sup>ˆ </sup>values from our simulation (i.e., where <em>n<sub>sim </sub></em>is the number of simulation runs; <em>θ </em>is <em>N </em>in this case, and <em>θ</em><sup>ˆ </sup>is either <em>N</em><sup>ˆ</sup><em><sub>LP </sub></em>or <em>N</em><sup>ˆ</sup><em><sub>C </sub></em>as both are ways to estimate <em>N</em>)<a href="#_ftn4" name="_ftnref4"><sup>[4]</sup></a>.

Estimate the bias of the Lincoln-Peterson and Chapman estimators, based on the results of your simulation. Is either estimator unbiased when <em>n</em><sub>1</sub><em>,n</em><sub>2 </sub>= 100?

<ol start="6">

 <li>Based on your findings, is the Lincoln-Peterson or Chapman estimator better? Explain your answer.</li>

 <li>Explain why the assumptions (a), (b), and (c) listed on the first page are unrealistic.</li>

</ol>

<a href="#_ftnref1" name="_ftn1">[1]</a> Interestingly, this estimator is also the maximum likelihood estimate. As you probably guessed, more complex versions of this idea have been developed since the 1600s.

<a href="#_ftnref2" name="_ftn2">[2]</a> Basically, you are empirically constructing the sampling distribution for <em>N</em><sup>ˆ</sup><em><sub>LP </sub></em>here. Remember the Central Limit Theorem which tells us the sampling distribution of the sampling mean? Each statistic has a sampling distribution and we are simulating it here (but using frequency instead of probability on the <em>y</em>-axis).

Page 2 of 3

<a href="#_ftnref3" name="_ftn3">[3]</a> Note that the sample size <em>n </em>does not appear in this equation. For an estimator to be unbiased, this property cannot depend on sample size.

<a href="#_ftnref4" name="_ftn4">[4]</a> Note: This procedure is not a replacement for a mathematical proof, but it’s a good way to explore statistical properties.

Page 3 of 3