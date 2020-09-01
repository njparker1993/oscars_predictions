# Predicting the Oscars with Machine Learning
<p align = 'center'>
<img src='images/osc_2020.png' width = '300'>
</p>

### Intro
The Oscars can be thought of as the Super Bowl of Hollywood. Movies come out each year, and are voted on not only by their merit, but they compete for favor of each voter in the Academy by campaigning. Stats like Genre, Money Made, or Rotten Tomatoes score are not enought to predict the Oscars, because art is subjective, and voting is personal. How can we predict the Oscars then? The strategy that has yielded the best results is by tracking awards shows throughout the year and using them as features to predict who will walk away with a little gold man statue.

### Data Acquisition
In my [scraping notebook](https://github.com/njparker1993/oscars_predictions/blob/master/scraping.ipynb), I scrape wikipedia to get the results of various awards shows such as the Golden Globes, Screen Actors Guild Awards (SAGs), British Film and Televsion Awards (BAFTAs), and more. Using the nomination and winner rates of the biggest award of each show, I predict who will take how the Best Picture Award. Scraping wikipedia idea and code came from github user [Buzdygan](https://github.com/Buzdygan). His colorful article on matter can found [here](https://blog.usejournal.com/predict-oscars-2019-with-data-science-356950b33a97)

### Modeling
My [final dataframe](https://github.com/njparker1993/oscars_predictions/blob/master/table_assembling.ipynb) for machine learning consisted of one row per film, and then 0/1 binary markers to designate if a film was nominated and if it won an award. For example, for the BAFTA's there was a 0/1 Bafta_nomination column and a 0/1 Bafta_win column. For my modeling, I used two approaches. The [first](https://github.com/njparker1993/oscars_predictions/blob/master/machine_learning_auto_ml.ipynb) uses H2O's Auto ML object to run through 20 models and pick the best one. The model is trained on years 1995 - 2014, and validated on 2014-2018. Once that model was chosen, it was re-trained on the full data set and used to predict 2019's nominees.

### Preferential Ballot Random Forest
The [second modeling strategy](https://github.com/njparker1993/oscars_predictions/blob/master/machine_learning_preferential_ballot.ipynb) was a more creative, and a bit more abstract. The way the real Oscars do their voting for best picture is through a process called a [preferential balloting system](https://www.youtube.com/watch?v=LjhoSv4Ood0). This works by instead of voting for one movie, voters rank all nominated movies, and movies are gradually crossed off that list until one film has over 50% of the 1st choice votes. 
I simulated this conveluted voting system by using DecisionTrees trained on different parts of the data. They had noise added to simulate bias, and each tree can approximately thought of as an Academy Voter. Each Tree produced one preferential ballot, and a winner was selected by elimnating films in the same way that the Academy's preferential balloting system would.

Here is an example of what one Tree would produce in my Preferential Balloting Random Forest method:
<p align = 'center'>
<img src='images/pb_rf_tree.png' width = '400'>
</p>
And here is how the votes from all the trees would be used to find the eventual winner using Preferential Balloting:
<p align = 'center'>
<img src='https://media.giphy.com/media/KZdQA9PquHywGpSXJF/giphy.gif' width = '300'>
</p>

### How effective will this modeling strategy be for simulating the Oscars? We will have to wait and see on Oscar Night Feb 9th! CHANGE TEST
