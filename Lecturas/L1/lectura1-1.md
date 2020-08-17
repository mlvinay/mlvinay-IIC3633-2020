# Resumen
The paper exposed by Sarwar et. al. of name "Item-based Collaborative Filtering Recommendation Algorithms", attempts to take a twist on the rather succesful collaborative filtering method, with the twist being of changing it's aproach. While the original uses user similarities for recommendations, Sarwar et. al. use the contrary, item similarities.

# The algorithm
The most important aspect it's to find the similarities between items, and to do that the researchers use the ratings given by users to items. Since a correlation is needed, one computes similarities of various items rated by the same users (for example, 3 users all rated object X). They also present 3 different similarities algorithm, those being cosine similarity, Pearson's similarity, and a "adjusted cosine similarity" which let's be honest, it's a cosine-Pearson mix.

Afterwards, for the prediction step one uses the user rating on various items, which weighted with the pre-computed relations it's either ponderated (weighted sum) or get's a regression to calculate/predict the user attraction to the item.

# The dataset
The researchers use the dataset from their (apparently) own website, MovieLens, a webpage for rating and getting recomended movies. One BIG mistake here, it's that the rating system it's not reported. Is it 1 to 5 stars? a value from 0 to 10? etc. This is important because of the measure of error used (MAE). If the rating system it's not reported, the quality of results it's just... relative to nothing.

# The results
As before mentioned, it's hard to say if the system results are absolutely good, but we can atleast be certain that on this dataset, the results are slightly better on most cases (different hyper-parameters). One thing that's not reported, it's the difference  Rec. Time/ Troughput on user-user v/s item-item models, which I believe to be a result of extreme importance, since it's one thing getting a better performance/quality, but the time? (This tradeoff is mentioned by the authors at the beggining of the paper).

# Conclusion
Using an item-item aproach it's more logical, atleast to me. If we talk about books, it makes more sense to recommend an item to a user because it's similar to another. For example, recomending Harry Potter to someone who liked Lord of the Rings? 

On the other side, there's a problem of "What happens to new users or new items". What if the same author of one book a user liked, realeses another, should the system wait for user ratings until actually recommending the book?

Naturally this algorithm it's quite old as of now (~19 years old), but if I had to give an idea right now to make this algorithm better, it would be using primal characteristics of the items to create characteristic vectors in a dimensional space, which are on close distance to other items (Again, Harry Potter and Lord of the Rings example, or two books of the same author). Furthermore, making a mix of primal characteristics and user ratings could prove even more benefitial.
