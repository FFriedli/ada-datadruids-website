---
layout: letter
---



# Dear Director,

Being one of our favorite directors, it's truly a shame that so much time has passed since your last film. We've heard
that a lack of inspiration is weighing you down, so we've decided to offer our help. Imagine this: a packed theater,
audiences glued to their seats, so captivated by the movie that they forget about their popcorn, and critics raving
about your latest masterpiece. What if we told you that the missing puzzle piece for creating such a blockbuster might
already be gathering dust on millions of bookshelves across the world, waiting to be brought to life?
You must constantly get story ideas from all kinds of people, and we bet it gets exhausting with everyone thinking they
know what makes a great script. Instead of crafting a half hearted plot of our own, we have decided to dive deep into
the great stories that already exist in the timeless form of books. By adopting our ideas, your next film has the
potential to stand among the greatest in cinematic history.
Book-based movies have a unique power: they can tap into an existing fanbase, provide a blueprint for the adaptation,
and have a proven track record of yielding more successful movies compared to non-book-based movies. We will explore how
such films outperform their bookless counterparts and uncover the most important factors to catapult your movie to the
top. From genre choice to popularity to narrative fidelity, we will tell you what factors to consider to turn the book
you choose into the next blockbuster.
But let’s start with a little game. Test your knowledge on successful movies in this quiz below. Do you see any pattern
in the movies outperforming their counterparts?

## Movie Revenue Quiz

<div style="display: flex; justify-content: center;">
    <iframe src="assets/quizz.html" 
            width="100%" 
            height="720px" 
            style="border:none; max-width: 1200px;">
    </iframe>
</div>

We will come back to how we matched these pairs for the quiz, but for now all you need to know is that all the winners
here are based on books whereas the others are based on a poem, a short film and traditional film scripts. We hope that
with that we have made you curious enough to keep reading about the world of book adaptations.


## Let us introduce you to our dataset

The first and maybe also most important step for a good data analysis is of course finding the data. We were equipped
with a lot of data on movies, containing not only metadata about its production but also movie summaries from Wikipedia
and IMDB-Ratings. We combined this data with a book dataset that includes important information such as Goodreads
ratings (the most important platform for book reviews, comparable to the IMDB website), the length of the book, release
date, author etc. It also includes which books were adapted to movies, allowing both datasets to be combined.
The first thing to do when handling such a big dataset is cleaning up. We chose to focus on movies that have information
about both the revenue and budget of the movie, which already shrunk our dataset to about 9000 movies. Out of these
9000, about 10 % are based on a book. In our analysis we will compare the data of movies-based-on-books with
movies-not-based-on-books.
You might have noticed that having to say “a-movie-based-on-a-book” or “a-movie-not-based-on-a-book” every time is quite
a mouthful. We want to make your life as easy as possible and will therefore introduce you to our good friends (aka.
acronyms) Bob and Nob. Bobs are all movies that are Based-On-a-Book. Nobs are all movies that are
Not-Originated-from-a-Book.
When we talk about Bobs, do you have some examples in mind? Some of the most successful movies ever made, both in terms
of revenue and ratings, are the Lord of the Rings, and to no one's surprise they are part of our Bobs! Can you find them
in the graph below? Can you find any other of your favorite Bobs?

<div style="display: flex; justify-content: center;">
    <iframe src="assets/plots/searchable_bob_revenue_vs_rating_js.html" 
            width="100%" 
            height="500vh" 
            style="border:none; max-width: 1200px;">
    </iframe>
</div>



## Matching

First, one has to define what it means for a film to be successful, which proves much harder than initially assumed.
Realizing that a movie is successful is easy, deciding whether it is more successful than another one is quite the
opposite. Is a small-budget artsy movie more successful than yet another Hallmark Christmas movie with the most
predictable storyline? Is a movie with hundreds of 5 star reviews better than a movie with thousands of 3 star reviews?
As often in life, the easiest thing is to copy what other people are doing, which leads us to two metrics, box office
revenue and ratings.

Merging the two metrics would significantly impact the outcome of any analysis, depending on the method of combination.
As a director, we’re quite sure that for you it is all about the money, nobody can eat a five star rating..
To get a first impression on our data, we could look at the evolution of revenue over time for both Bobs and Nobs. When
talking about money over time, it is important to consider that some effects are simply caused by inflation. We have
therefore adjusted the revenue for inflation, using the US consumer price index. For all subsequent analysis we have
always used an inflation-adjusted scale for all money related things.

<div style="display: flex; justify-content: center;">
    <iframe src="assets/plots/adj_revenue_over_time_js.html" 
            width="100%" 
            height="450vh" 
            style="border:none; max-width: 1200px;">
    </iframe>
</div>



Example with custom html :
<div style="display: flex; justify-content: center;">
    <iframe src="assets/plots/zzz_check_with_html_self_code_222.html" 
            width="100%" 
            height="450vh" 
            style="border:none; max-width: 1200px;">
    </iframe>
</div>

We can already see that while both revenues for Bobs and Nobs increase over time, Bobs have always made more money than
Nobs.
However, this simple analysis does not reliably show whether the observed trend is simply due to the Bobs being based on
books. When talking about money, we also have to consider how much was spent.

<div style="display: flex; justify-content: center;">
    <iframe src="assets/plots/adj_budget_over_time_js.html" 
            width="100%" 
            height="450vh" 
            style="border:none; max-width: 1200px;">
    </iframe>
</div>


So Bobs not only generated more revenue but were more expensive on average than Nobs. So what if we look at the profit
they made?



<div style="display: flex; justify-content: center;">
    <iframe src="assets/plots/adj_revenue_budget_over_time_js.html" 
            width="100%" 
            height="450vh" 
            style="border:none; max-width: 1200px;">
    </iframe>
</div>


That’s great to see! Bobs have made more profit on average than Nobs.

But this alone is probably not enough to convince you of directing a Bob. What if the effect is caused by so-called
confounders? Maybe Bobs are outperforming Nobs because of the chosen genres? We want to convince you without a doubt
that choosing a Bob for your next masterpiece is a good idea, so we should take care of these confounders first.

In order to get more meaningful results we performed a matching analysis. The aim of this statistical method is to
compare Bobs and Nobs with similar preconditions for achieving high box office revenue, thereby minimizing the impact of
confounding factors. This necessitates the definition of what it means for two films to have similar preconditions to
success. To make sure that we catch all important factors we not only fitted one but two models: linear regression and
random forests.
While we try to give you as much information as needed to understand our findings, we won’t bore you with any technical
details of the models we used, we promise. As data analysts, it’s our job to handle the technical stuff so you don’t
have to.

Linear Regression tries to model the data by defining the impact of each variable on the outcome. As an example, if our
data included the total number of cookies consumed during filming, this would probably have a very low impact on the box
office revenue. The duration of the movie on the other hand will probably have some influence. Be it that longer movies
seem to give more bang for the buck and thus attract more viewers, or that shorter movies can be played more often in
cinemas. Deciding on which scenario is more important is where linear regression comes in.
We fitted three models in total: once on all our movies, once only on Bobs and once only on Nobs. With this approach we
wanted to investigate which factors influence all movies equally and which factors influence Bobs differently than Nobs.


> TODO: add linear regressoin parameters plot




In the plots you can see all features, out of the almost 50 we tested, that have significant p values. One thing that is
immediately noticeable is that the confidence intervals (the orange lines) for our Bobs are much bigger than for Nobs
and the entire dataset. While not ideal, this can easily be explained by the fact that our dataset for Bobs is much
smaller than for Nobs. This makes the output more noisy and the predictions less confident. In an ideal world we would
expand our dataset on Bobs, but we will do our best to work with what we have.
Any points that are on the right side of the dashed line have a positive effect on the revenue prediction, on the left
side the effect is negative. A high vote count seems to have the highest positive effect on the revenue, together with
the adjusted budget. The popularity measure is particularly important for our Bobs. It is a measure of how often the
movie has been looked up lately on the IMDB website. Surprisingly, the movie year has a negative effect on the revenue,
meaning that if we isolate the effect of the release date, newer movies perform worse than older ones. We explain this
to ourselves with the fact that nowadays there are a lot of bad movies (not from you of course) that make no profit at
all, while in the past, movie making was more of an exclusive art form, where much less movies were made. So while there
are a few great movies with a lot of revenue nowadays, there are even more really bad ones, leading the newer release
years to have a negative effect on the revenue.

There seems to be some genres like Thrillers that are specifically suitable for the success of Bobs but not for Nobs.

Linear regression is an easy to use and fast method to gain some insight into the dataset. However, as the name
suggests, it can only capture linear relationships between our data and the revenue. To give you a more varied insight
into our data we decided to additionally use random forests to extract feature importances and confirm our previous
findings. .

While the name “random decision forest” sounds spooky, its working principle is quite easy to understand. It consists of
many different decision trees that are essentially interviewing the data. A decision tree might ask whether a movie has
been produced in the US and depending on the answer it will then either try to identify in which other country this
movie was produced, or move on to some other questions like the number of languages the movie was translated to. A tree
will normally ask between 10 and 20 questions. Afterwards, every tree makes its own estimate of the revenue of the
movie. Each tree tries to have the best estimate possible. Having many of these trees then allows the algorithm to check
which questions are being asked the most often, which directly gives their impact on the prediction of the revenue.



> plot of random forest feature importance



Again we can see that the vote count and budget is very important for the success of a movie. Popularity is also again
more important for Bobs than Nobs, the same for the Thriller genre.

While both models are not perfect for the prediction of a movie's revenue, they still show a clear pattern of which
parameters are important for a movie's success.
Some of these features have a positive effect on the success of the movies and others have a negative effect.










---


### Popularity of Movies vs books

<div style="display: flex; justify-content: center;">
    <iframe src="assets/plots/popularity_over_time_js.html" 
            width="100%" 
            height="450vh" 
            style="border:none; max-width: 1200px;">
    </iframe>
</div>





