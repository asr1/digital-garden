---
{"dg-publish":true,"permalink":"/software-and-technology/using-ai-for-prison-reform/","tags":["politics","technology","ai"],"noteIcon":1}
---


c.f. [Police are Using DNA to Generate 3D images of Suspects They've Never Seen](https://www.vice.com/en/article/pkgma8/police-are-using-dna-to-generate-3d-images-of-suspects-theyve-never-seen) and [Machine Bias](https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing)

The COMPAS system from the article is extremely flawed: it models based on factors that correspond extremely highly with race and poverty, so it's not surprising that it is wrong in the way that it is so often.

But, making an algorithm for this is extremely tricky. There's two ways to analyze a prediction. The Machine Bias article used reverse analysis: first they find what the outcome was, then they match it to what the prediction was. In this case, they looked at people who were were not arrested a second time within the two-year window, and found that black people had higher COMPAS (risk) scores than white people. That's a bad look, for sure!

The other way we can look is with forward analysis (what the prediction had to use). In other words, are we consistent when assigning a number: does a white person with a COMPAS of 3 have the same recidivism risk as a black person with a COMPAS of 3?

You can optimize for forward or reverse analysis, but only one of them. If you have two populations (black, white) and they have different rates of exposure to the algorithm (in this case arrest rates), they WILL be wrong either forward or backwards: either a white person's 5 will mean something different than a black person's 5, OR black people who aren't re-arrested will have higher scores than people who do.

It's a messy problem, and part of the mess is that we arrest WAY more black people than we do white people. And I'm 100% not trying to defend this (and ESPECIALLY not trying to defend the 3d modelling BS from the headline).

TL;DR: STOP USING ALGORITHMS FOR THINGS LIKE THIS! Racism in -> racism out.

## See Also

[Brave New Planet: What Algorithms Say About You](https://www.bravenewplanet.org/episodes/what-algorithms-say-about-you)

[Police are Using DNA to Generate 3D images of Suspects They've Never Seen](https://www.vice.com/en/article/pkgma8/police-are-using-dna-to-generate-3d-images-of-suspects-theyve-never-seen)

[Machine Bias](https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing)