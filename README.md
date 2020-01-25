# oscars_predictions

The Oscaras can be thought of as the Super Bowl of Hollywood. Movies come out each year, and are voted on not only by their merit, but they compete for favor of each voter in the Academy by campaigning. Stats like Genre, Money Made, or Rotten Tomatoes score are not enought to predict the Oscars, because art is subjective, and voting is personal. How can we predict the Oscars then? The strategy that has yielded the best results is by tracking awards shows throughout the year and using them as features to predict who will come how with a little gold man statue.

### Data Acquisition
In my scraping notebook, I scrape wikipedia to get the results of various awards shows such as the Golden Globes, Screen Actors Guild Awards (SAGs), British Film and Televsion Awards (BAFTAs), and more. Using the nomination and winner rates of the biggest award of each show, I predict who will take how the Best Picture Award. Scraping wikipedia idea and code came from github user [Buzdygan](https://github.com/Buzdygan). His colorful article on matter can found [here](https://blog.usejournal.com/predict-oscars-2019-with-data-science-356950b33a97)

### Modeling
My final dataframe for machine learning consisted of one row per film, and then 0/1 binary markers to designate if a film was nominated and if it won an award. For example, for the BAFTA's there was a 0/1 Bafta_nomination column and a 0/1 Bafta_win column. For my modeling, I used two approaches.
