# Abstract
This lecture takes about a matrix-fitting aproach to netflix rating challengue (with train data 100M ratings for 17K movies from 500K users). Basically, it creates a characteristic space of arbitrary length (cause why not 40) that tries to describe movies. So, each movie has it's own characteristics vector, and each user has it's own preference vectors (of same length due to obvious reasons) and the prediction it's the dot multiplication of said vectors (user preference * movie characteristics).

# The algorithm (for training)
It's backprop. It's just backprop. It's literally randomly initializing every vector and taking a gradient step (ehem, error) with a static learning rate which the author seems to have a "I don't wanna change the learning rate" trauma. Also there's a baseline prediction thing that I couldn't find it's use. It's understandable as a baseline, but where does it go on this machine learning thing?

# Fixes over fixes
Oh, there's also a Tikhonov regularization thing going on in order to prevent overfitting. Basically it changes the gradient (the error) adding some memory into it. If you are updating a user vector, you diminish the error by a small amount of the k-1 value of the user vector.

There's the author add's a non linealization function to the prediction. Instead of being user_pref * movie_char, it's G(user_pref * movie_char), with G being some non-linear function. The author proposes two, sigmoid and clipping (keeping the values between in a range)

# Results
Since this "paper" does not aim to compare, it's not possible to say that the results are either good or bad. I mean, they did get 3rd place in the challengue though. Anyway, the user comments mostly  in the results about overfitting and regularization as the results actually show, that the error actually goes up again if one trains for to many epochs.

# Conclusion
Almost everything here, it's relatable to a neural network kind of thing. You have two set of vectors (which could be two layers) that you dot product in order to get a prediction. That's a 2-layer deep neural network. Kind of. There's no input really as the first layer it's actually the input? Anyway, there's non-linear functions in this, and considering sigmoid being a popular activation function in deeplearning (+ ReLu it's kind of similar to clipping), taking overfitting into consideration, etc etc. This machine learning algorithm developed by the author, can't help to remind me of a neural network but in a lot of ways.