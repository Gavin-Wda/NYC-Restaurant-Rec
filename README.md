<img src="banner_locals_NewYork.jpg" alt="NYC Banner">

# NYC-Restaurant-Recommendation-System-For-‘Tripadvisor’

Overview 

The goal of this project was to process mutiple features pretaining to individual restaurant reviews in order to generate potential recommendations based on user inputs. The data used comes from Tripadvisor, covering thousands of establishments across the city, with customer generated content. The end system implements vectorization of these features and provides a list of similar restaurants based off of cosine_similarity scores. 

Understanding / Context 

New York City, otherwise known as the concrete jungle, is the most densely populated city in the United States. Given this, it is no surprise that there are over 20,000 restaurants across the city, according to data from OpenTable. Thus, even though you may have one spot you know and love, it may be hard to discover other spots or get solid recommendations. Now, one could scour the internet looking over names, comments, reviews, and food categories, but it would be nice to have a system that generates spots for you. - Such a system would do nicely on a site like Tripadvisor, using its own data to do so. That is the purpose of this project. 

Data Understanding 

The New York City Restaurants Dataset contains over 10,000 entries from Tripadvisor. Each entry contains the restaurant title, reviews, relevant categories, comments,  popular foods, and whether or not it has online ordering. In preparation for the system, a heatmap for null values was used to discover patterns. In doing so it was found that many entries that were missing a review value were also missing comments. These rows were filtered out using a boolean mask as they were not very useful entries. Any remaining null values in the comments column were filled with null strings so that they could still be used based on their other factors. Furthermore, the Online Order column was found to be missing nearly half of its entries and was not relevant to the system's needs so it was removed. Finally, the dataset’s index was reset and then added as a column that would be used for referencing purposes later on. 

System and Evaluation 

For this system to work, the relevant fields for forming recommendations needed to be congregated to single entries. These included the Title, Category, Comments, and Popular Food columns. Once done, a vectorizer was created and used to form feature vectors, allowing the use of the cosine_similarity function, giving us the basis for the system. With input from the user of their favorite restaurant I was able to ensure the match using difflib, create a list of similar restaurants with enumerate, sort it in descending order, and then run it through a  for loop that generates the top entries of the list using the matching index column created earlier. - Upon the first run, it appeared to work as intended, listing ten restaurant recommendations based on the user’s input. However, with certain entries it became clear that what was not taken into account was the possibility of multiple reviews of the same restaurant. This would lead to a list of ten recommendations for the same spot. Thus, what felt like the simplest solution was putting an if statement within the if statement so that it did not process the entry if the name matched the user’s input value, moving to the next one in the list. 

<img src="NYC System.png" alt="NYC Banner">

Conclusion 

This restaurant recommendation system works quite well given its purpose and could be implemented for use. I do believe that given more reviews, more data points, and more locations in general, the better and more useful it will be. I would also consider the removal of fast food chains for the sole reason that  people do not require a system to get them on their radar. They are fairly universal as it is. In addition, this system does not have to be limited to New York City given Tripadvisor’s widespread usage. It would be ideal for the user to limit their search to an area(if added), price range(if added), and/or type(if added), thus filtering the results, increasing usability. 

Link to Dataset:

https://www.kaggle.com/datasets/rayhan32/trip-advisor-newyork-city-restaurants-dataset-10k/data?select=trip+advisor+restaurents++10k+-+trip_rest_neywork_1.csv

