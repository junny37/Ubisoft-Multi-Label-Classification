<img src="http://imgur.com/1ZcRyrc.png" style="float: left; margin: 20px; height: 55px">

# CAPSTONE : Ubisoft's Skull & Bones
----

## Background & Problem Statement


[Ubisoft](https://www.ubisoft.com/en-us/company/about-us) is a leading company in the gaming industry. Some [popular games](https://www.thegamer.com/ubisoft-best-games/#assassin-rsquo-s-creed-4-black-flag) include the famous Assassin's Creed series, Far Cry, Tom Clancy, as well as Rayman, just to name a few. Ubisoft has been developing a new game over the past couple of years, called "Skull & Bones". This upcoming game was [inspired by their most popular Assassin's Creed series, "Assassin's Creed IV: Black Flag"](https://screenrant.com/skull-and-bones-best-game-recommendations/).

The upcoming game, [first announced in 2017](https://www.pcgamer.com/ubisoft-announces-skull-and-bones-an-open-world-multiplayer-pirate-game/) has been delayed multiple times, and most recently [delayed till 2024](https://www.thumbculture.co.uk/skull-and-bones-misses-march-release). Ubisoft has released a statment saying they would want to "showcase a much more polished and balanced experience" in their game.

Ubisoft currently has not been addressing much of user's reviews and feedback for game improvement. Posing as someone who is working for Ubisoft's data team, I am interested in  <font color = 'green'>**looking into the reviews of Assassin's Creed IV: Black Flag, and using Data Science to get insights from reviews to identify topics which reviews talk about** </font>. This is so Ubisoft can further improve those particular elements of their game, as well as include and improve the appropriate elements for their upcoming Skull & Bones game, to match the polished standard they are looking for.

For this project in particular, I will be using OneVsRestClassifier, ClassifierChain, and LabelPowerset as the developing models to perform multi-label classifications. Since the data that was retrieved from Steam does not have a column with specific topics in each review, we will first use an unsupervised model to obtain the labels so we have a result column to compare our results to.


## Data Dictionary

|Feature|Type|Description|
|---|---|---|
|num_games_owned|int|number of games owned by the user|
|num_reviews|int|number of reviews returned in this response|
|playtime_forever|float|total playtime of game|
|playtime_last_two_weeks|float|playtime in the last two weeks|        
|playtime_at_review|float|playtime when the review was written|
|last_played|datetime|time for when the user last played|
|review|object|text of written review|
|timestamp_created|datetime|date the review was created|
|recommended|int|1 means it was a positive recommendation|
|votes_up|int|the number of users that found this review helpful|
|votes_funny|int|the number of users that found this review funny|
|weighted_vote_score|float|helpfulness score|
|comment_count|int|number of comments posted on this review|   
|steam_purchase|bool|whether it was a steam purchase|        
|received_for_free|bool|whether user received the game for free|         
|written_during_early_access|bool|whether the review was written during early access release|


## Conclusion

Using F1 score as the performance metric, the main aim is to have a classifier with the ability to correctly perform multi-label classification on as many labels as we can.

As such, we can conclude that the One Vs Rest Classifier using Logistic Regression performed the best, with 4 labels in the test set having an F1 score above 60%. Moreover, 2 of those labels could perform close to or above 80%.

Therefore, we are able to use the One Vs Rest Classifier with Logistic Regression to identify reviews with the labels 'graphics', 'combat', 'pirate theme' and 'storyline' confidently.

Ubisoft can then use this to identify from the reviews, what specific topics people addressed. As such, this can help the team's game developers identify and solve certain issues, or continue to provide what the consumers want. The marketing and PR team can also use this information to release appropriate statements addressing these specific topics, ensuring that Ubisoft does care about their consumers.


## Future Improvements

There are many things that can be improved with this model. The aim in the future is to be able to have all labels' F1 score at a decent percentage so it can be used for new reviews to correctly identify topics mentioned.

One way the model can be improved is to have more data. As our previous unsupervised model took up a lot of time and money, not all the data was able to be run through the model. Future works would be to: 
1) Run through all the rows and label all of them using unsupervised model
2) Narrow down all the labels into the top used labels
3) Run the prompt through the unsupervised model again with a list of specific labels.

Compared to just running through a sample and the top weighted reviews.