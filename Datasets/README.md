# Steps for Creating Datasets

## English Dataset

## Bokmal Dataset

## Preprocessing in Weka (3.8.3), Bokmal
On April 16, 2019, I began by uploading the Bokmal .csv dataset into Weka (a machine learning software). The character_name column was set as the attribute class. Using a RemoveByValue filter in the preprocessing screen, I removed all character names except for Nora and Helmer.

Still in the preprocessing screen, working with the character_speech column, I converted the column from Nominal to String and then from StringToWordVector. I chose to set the word frequency to 5 (meaning that a word must occur 5x to be pulled). I also set it so only 50 words appeared in the output.

Then, still in the preprocessing screen, I added another filter, AddClassification, and used Logistic Regression as a classifier. This created a distribution for both Nora and Helmer. I once again set character_name to be the attribute class. This new dataset was then saved as a .csv named "Weka_Edited_Bokmal.csv"

## Preprocessing in Weka (3.8.3), English
