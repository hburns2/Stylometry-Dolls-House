# Steps for Creating Datasets

## English Dataset

## Bokmal Dataset

## Preprocessing in Weka (3.8.3), Bokmal
On April 16, 2019, I began by uploading the Bokmal .csv dataset into Weka (a machine learning software). The character_name column was set as the attribute class. Using a RemoveByValue filter in the preprocessing screen, I removed all character names except for Nora and Helmer.

Still in the preprocessing screen, working with the character_speech column, I converted the column from Nominal to String and then from StringToWordVector. I chose to set the word frequency to 5 (meaning that a word must occur 5x in the entire text to be pulled). I also set it so only 50 words appeared in the output.

Then, still in the preprocessing screen, I added another filter, AddClassification, and used Logistic Regression as a classifier. This created a distribution for both Nora and Helmer, added as columns within the dataset. I once again set character_name to be the attribute class. This new dataset was then saved as a .csv named "Weka_Edited_Bokmal.csv".

This "Weka_Edited_Bokmal.csv" dataset has 56 columns and 812 rows. Each column stands for a word, in Norwegian, save for the last 3. The last three columns are "distribution_nora," "distribution_helmer," and "character_name" (the class attribute). The information contained in the rows (save for the last 3 columns) are the number of times the word is mentioned per line. All numbers present in the rows are less than 10, meaning that each word appears less than 10 times per character line.

## Preprocessing in Weka (3.8.3), English
On April 16, 2019, I began by uploading the English ascii edits .csv dataset into Weka. The character_name column was set as the attribute class. Using a RemoveByValue filter in the preprocessing screen, I removed all non-essential characters, keeping only the people who spoke more than 100 times. This left only Nora, Helmer, Mrs. Linde, Krogstad, and Rank.

Still in the preprocessing screen, working with the character_speech column, I converted the column from Nominal to String and then from StringToWordVector. I chose to set the word frequency to 5 (meaning that a word must occur 5x in the entire text to be pulled). I also set it so only 50 words appeared in the output.

Then, still in the preprocessing screen, I added another filter, AddClassification, and used Logistic Regression as a classifier. This created a distribution for all characters, added as columns within the dataset. I once again set character_name to be the attribute class. This new dataset was then saved as a .csv named "Weka_Edited_English.csv".
