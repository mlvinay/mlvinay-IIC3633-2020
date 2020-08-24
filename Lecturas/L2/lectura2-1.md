# Abstract
The paper exposed by Hu Y. et al. takes an aproach to implicit rating using a novel model, that while it may look a bit similar to latent factor models (for example those who use SVD), it's results are quite different

# The algorithm
The initial aproach it's similar to funkSVD, as there's a user preference matrix X (where X<sub>u</sub> denotes it's user column), and an item characteristic matrix Y (where Y<sub>i</sub> denotes it's item column). It's point product it's set in a quadratic difference with a user-item preference factor, difference which becomes most of the cost function that one tries to reduce. This user-item factor it's considereded as a binary measure of the indirect rating (with the rule of being 1 if r<sub>ui</sub> it's bigger than 0, 0 otherwise). Furthermore, this cost to be reduced it's multiplied by a confidence factor which kind of looks like this <img src="https://render.githubusercontent.com/render/math?math= c_{ui} = 1 + \alpha \frac{log(1+r_{ui}}{\epsilon})">.

Finally, the author considers adding a regularization by adding the module-2 of the column vectors multiplied by a lambda constant (a quite common regularization trick).

# Results
The results showed are... hard to discuss to say the least. It's not that the results are bad, they actually appear quite good. The thing is, the authors had to create their own measure to evaluate their model, which by their own words "it's not reliable". Furthermore, the model is described as to fit various datasets (not related to the item it's trying to recomend), it's only tested on one dataset. While this is more than understandable due to the paper being written 12 years ago, and having an "Official" implicit rating training + testing set it's counterintuitive. Yet, one cannot but hope for more results.

# One thing in particular
The rank system used, uses rank 0% as the best result. So when the mean rank (which is used as the evaluation measure) it's lower, it's better. Wouldn't it had been more intuitive to do the contrary, using a value of 100 for the most reccommended value? If one uses an r<sub>ui</sub> that relates to how many times a show/movie has been watched, I believe to be more intuitive to have big numbers multiplying big numbers and small numbers multiplying small numbers. 