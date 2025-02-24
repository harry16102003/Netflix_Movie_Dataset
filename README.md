# Netflix_Movie_Dataset

### Data Loading and Initial Exploration:
* Libraries: The analysis started by importing necessary libraries: numpy, pandas, matplotlib.pyplot, and seaborn.
* Dataframe Creation: A Pandas DataFrame (df) was created by reading the mymoviedb.csv file. The lineterminator argument was used to handle potential issues with line endings in the CSV file.
* Initial Inspection: The head() method was used to display the first few rows of the DataFrame, providing a glimpse of the data's structure and content.
* Data Information: The info() method was used to get a summary of the DataFrame, including data types, non-null counts, and memory usage. This helped in understanding the completeness and nature of the data.
* Exploring the 'Genre' Column: The head() method was applied to the 'Genre' column to examine its contents and structure.
* Duplicate Check: The duplicated().sum() method was used to identify and count any duplicate rows in the DataFrame.
* Summary Statistics: The describe() method was used to calculate summary statistics (mean, standard deviation, min, max, quartiles) for numerical columns, providing insights into the distribution and range of values.

### Data Cleaning and Transformation:
* Date Conversion: The 'Release_Date' column, initially of object type, was converted to datetime objects using pd.to_datetime(). Then, the year was extracted from the datetime objects.
* Column Removal: Irrelevant columns ('Overview', 'Original_Language', 'Poster_Url') were dropped from the DataFrame using df.drop().
*Categorizing 'Vote_Average':
1. A function categorize_col was defined to categorize a given column based on its quartiles.<br>
2. The describe() method was used within the function to calculate the quartile edges for categorization.<br>
3.The 'Vote_Average' column was categorized into 'not_popular', 'below_avg', 'average', and 'popular' based on its distribution.
* Genre Column Handling:<br>
The 'Genre' column, which contained comma-separated values, was split into individual genres using df['Genre'].str.split(', ').<br>
The explode() method was used to transform each row with multiple genres into multiple rows, each with a single genre.<br>
The 'Genre' column was converted to the 'category' data type to improve memory usage and performance.<br>
* Handling Missing Values: The dropna() method was used to remove rows with missing values (NaN) from the DataFrame. The isna().sum() method was used to verify that all missing values had been removed.

### Data Analysis and Visualization:
* Most Frequent Genre:
The describe() method was used to get a summary of the 'Genre' column, including the most frequent genre.
A count plot was created using seaborn.catplot() to visualize the distribution of movies by genre. The genres were ordered by their frequency using df['Genre'].value_counts().index.
* Vote Average Distribution:
The value_counts() method was used to count the occurrences of each category in the 'Vote_Average' column.
A count plot was created using seaborn.catplot() to visualize the distribution of movies by vote average category. The categories were ordered by their frequency.
* Highest and Lowest Popularity Movies:
Boolean indexing was used to find the movie(s) with the highest popularity using df[df['Popularity'] == df['Popularity'].max()].
Similarly, boolean indexing was used to find the movie(s) with the lowest popularity using df[df['Popularity'] == df['Popularity'].min()].
* Most Filmed Year:
A histogram was created using df['Release_Date'].hist(bins=20) to visualize the distribution of movies by release year.

### 4. Conclusions:
* Most Frequent Genre: Drama is the most frequent genre of movies released on Netflix.
* Vote Average: The 'average' category has the highest votes in the 'Vote_Average' column.
* Highest Popularity: "Spider-Man: No Way Home" has the highest popularity.
* Lowest Popularity: "The United States vs. Billie Holiday" has the lowest popularity. "Threads" also shares the same lowest popularity score.
* Most Filmed Year: 2020 has the most filmed movies.
