# Perspective-API-Bias

Hypothesis:

My hypothesis for finding a bias in Google’s Perspective API is that “The average collective score of reviewed comments that attack Islam is greater than the collective score of reviewed comments that attack Christianity.”.

Thresholds/Definitions:
- “False Positives” are comments scored at >=70% but do not show significant offense. This is the threshold suggested by the Perspective API for checking false positives.
- “False Negatives” are comments scored at  >=35% and <70% but show offense. This is the threshold for comments about Christianity. The lower threshold is 35% because there are so few comments about Christianity. The threshold for comments about Islam was >=15% and <70% because there were so few comments about Islam.
- “Likely Toxic” comments have a score >=70%. I use this label because the Perspective API will have false positives, and, according to the API docs,  the percentages present how many out of 10 people might find the comment offensive
- “Less-Likely Toxic” comments have a  score of >=35% and <70%. I use this label because the Perspective API will have false negatives, and, according to the API docs,  the percentages present how many out of 10 people might find the comment offensive


Method:

The dataset that was used to test the Perspective API is a .csv file of 41,338 comments from Wikipedia that have already been run through the API. I created a list of comments that contained comments with at least one of the following words or their lowercase versions: “Islam”, “Muslim”, “Christianity”, and “Christian”. I then ran that list through the API, putting the comments and their scores in separate lists. I then created a data frame for each type of comment; one for comments about Islam and one for comments about Christianity. I then filtered both data frames with the previously mentioned thresholds to search for false positives and false negatives. I searched by reviewing the same amount of comments for each data frame.

Next, I calculated the total averages of the comments I reviewed for each data frame to test my hypothesis. Lastly, I calculated the false positive/false negative rates for each set of comments I reviewed. I also ran a few of my own queries through the API, separate from the other comments.


Results/Conclusions:

The result found after conducting tests is that the collective average score for comments against Christianity is greater (Christian Average = 74.75 | Islam Average = 61.2). This may be because there was a significantly greater amount of comments about Christianity before processing which possibly allowed for more opportunity to find “Likely Toxic” comments against Christianity.

Another result found from testing is that the False Negative and False Positive rates for comments against Islam and Christianity are the following:

- False Positive Rate (Islam) = 0% & False Negative Rate (Islam) = 60%
- False Positive Rate (Christianity) = 25% & False Negative Rate (Christianity) = 50%

These rates show that Perspective is more likely to miss-label comments against Islam or Muslims as “Less-Likely Toxic”, and miss-label comments against Christianity and Christians as “Likely Toxic”. My theory for the miss-labeling of comments against Christianity is that there were many obscene and inappropriate words used in those comments, but, since Perspective does not use context in its scoring algorithm, it is assumed those words are meant to attack Christianity. My theory for the miss-labeling of comments against Islam is that Perspective did not test with enough comments about Islam, lacking a significant amount of data to more accurately score those types of comments.

The original queries I made to test the Perspective algorithm resulted in comments against Islam and Muslims scoring higher than those against Christianity and Christians.

- Muslim scores = 96% & 80%
- Christian scores = 91% & 76%
