# Steps for Creating Datasets

## English Dataset
I began by taking the .txt version of the script and opening it in a Jupyter Notebook called "Creating_Datasets-English.ipynb." The first element of my cleaning process involved using regular expressions to remove all text within parentheses. Text within parentheses are indicative (in the case of this version of the script) as stage directions. The regular expression created was built with assistance from Elizabeth Wickes (Github: elliewix). Then, exploiting the structure of the document, I split the text on every double newline.

From there, I was able to use indexing to determine the start and the end of the script, creating a new variable that held only the character names and their corresponding speeches. I took this time, using the imported string package, to lowercase all text and remove punctuation.

Then, my goal was to create 2 lists: one of character names and one of their respective speeches. In the first list, the character names, I once again was able to exploit the structure of the text. The character names were always the first element of each string. However, this failed with names containing 2 parts (i.e. Mrs. Linde). I went back to before I split the text and added a regular expression that would take each instance of the name "Mrs. Linde" and transform it into "MrsLinde." Due to this transformation, I was then able extract the character names as I needed.

I then created a list of character speeches, pulling only the lines with a length greater than 1. These two lists were then zipped together (and newline characters were removed) and then exported to a .csv named "characters_and_speeches-English.csv."

Some additional cleaning still needs to occur. The character names are still part of the character speech elements. I cannot simply remove all mentions of a name, for names also occur within the speech itself. I plan to extract that information by splitting the speech elements on spaces and removing the first element. This will cause the output to include brackets and apostrophes due to the nature of the list. I would be able to find/replace these elements once the dataset is in .csv form.

## Bokmal Dataset
I began by taking the .txt version of the script and opening it in a Jupyter Notebook called "Creating_Datasets-Bokmal.ipynb." The first element of my cleaning process involved using regular expressions to remove all text within parentheses. Text within parentheses are indicative (in the case of this version of the script) as stage directions. The regular expression created was built with assistance from Elizabeth Wickes (Github: elliewix). Then, exploiting the structure of the document, I split the text on every double newline.

From there, I was able to use indexing to determine the start and the end of the script, creating a new variable that held only the character names and their corresponding speeches. I took this time, using the imported string package, to lowercase all text and remove punctuation.

Then, my goal was to create 2 lists: one of character names and one of their respective speeches. In the first list, the character names, I once again was able to exploit the structure of the text. The character names were always the first element of each string. However, this failed with names containing 2 parts (i.e. Fru Linde). I went back to before I split the text and added a regular expression that would take each instance of the name "Fru Linde" and transform it into "FruLinde." Due to this transformation, I was then able extract the character names as I needed.

I then created a list of character speeches, pulling only the lines with a length greater than 1. These two lists were then zipped together (and newline characters were removed) and then exported to a .csv named "characters_and_speeches-Bokmal.csv."

To import into Weka, however, further cleaning was needed. The data was output as utf-8 due to the special characters that exist within the language. With the assistance of Dr. Vetle Torvik, the .csv file was converted to ascii. While this results in the loss of special characters, it was necessary to be able to import the data. Additionally, many of the Bokmal words contain punctuation within the words. This was removed using find/replace in Excel, replacing the apostrophes with nothing. As before, with this, some information ended up being lost. However, it was decided that combining these parts into one word instead of two was the best option in this case. This updated .csv file was saved as "characters_and_speeches-Bokmal_ascii-Edits.csv."

Some additional cleaning still needs to occur. The character names are still part of the character speech elements. I cannot simply remove all mentions of a name, for names also occur within the speech itself. I plan to extract that information by splitting the speech elements on spaces and removing the first element. This will cause the output to include brackets and apostrophes due to the nature of the list. I would be able to find/replace these elements once the dataset is in .csv form. Additionally, not all elements of Fru Linde were caught using my regular expression, so I need to further investigate why this might be.

## Preprocessing in Weka (3.8.3), Bokmal
On April 16, 2019, I began by uploading the Bokmal ascii edits .csv dataset into Weka (a machine learning software). The character_name column was set as the attribute class. Using a RemoveByValue filter in the preprocessing screen, I removed all character names except for Nora and Helmer.

Still in the preprocessing screen, working with the character_speech column, I converted the column from Nominal to String and then from StringToWordVector. I chose to set the word frequency to 5 (meaning that a word must occur 5x in the entire text to be pulled). I also set it so only 50 words appeared in the output.

Then, still in the preprocessing screen, I added another filter, AddClassification, and used Logistic Regression as a classifier. This created a distribution for both Nora and Helmer, added as columns within the dataset. I once again set character_name to be the attribute class. This new dataset was then saved as a .csv named "Weka_Edited_Bokmal.csv".

This "Weka_Edited_Bokmal.csv" dataset has 56 columns and 812 rows. Each column stands for a word, in Norwegian, save for the last 3. The last three columns are "distribution_nora," "distribution_helmer," and "character_name" (the class attribute). The information contained in the rows (save for the last 3 columns) are the number of times the word is mentioned per line. All numbers present in the rows are less than 10, meaning that each word appears less than 10 times per character line.

## Preprocessing in Weka (3.8.3), English
On April 16, 2019, I began by uploading the English dataset into Weka. The character_name column was set as the attribute class. Using a RemoveByValue filter in the preprocessing screen, I removed all non-essential characters, keeping only the people who spoke more than 100 times. This left only Nora, Helmer, Mrs. Linde, Krogstad, and Rank.

Still in the preprocessing screen, working with the character_speech column, I converted the column from Nominal to String and then from StringToWordVector. I chose to set the word frequency to 5 (meaning that a word must occur 5x in the entire text to be pulled). I also set it so only 50 words appeared in the output. From there, I removed any names from the output (i.e Torvald, Nora) as well as any non-words from the cleaning process (i.e s, t). The "don" was left in, because I was aware this word was actually "don't."

Then, still in the preprocessing screen, I added another filter, AddClassification, and used Logistic Regression as a classifier. This created a distribution for all characters, added as columns within the dataset. I once again set character_name to be the attribute class. This new dataset was then saved as a .csv named "Weka_Edited_English.csv".

This "Weka_Edited_English.csv" dataset has 53 columns and 1250 rows. Each column stands for a word in English save for the last 6. The last six columns are "distribution_nora," "distribution_helmer," "distribution_mrslinde," "distribution_krogstad," "distribution_rank," and "character_name" (the class attribute). The information contained in the rows (save for the last 6 columns) are the number of times the word is mentioned per line. All numbers present in the rows are less than 10, meaning that each word appears less than 10 times per character line.
