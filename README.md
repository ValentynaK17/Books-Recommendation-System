# Book Recommendation System
Building of a Book Recommendation System, based on user and book interactions represented in rating scores. The system should help both:
 - *book readers* to discover great content quickly,
 - *businesses* with assiting in increasing sales or engagement levels on their platforms. <br>

The system combines:
 - Non-Personilized approach, suggesting brand new users Top Rated books within statistically significant subset
   <p align="center">
   <img src="https://github.com/ValentynaK17/Books-Recommendation-System/blob/main/Output/Non_Personilized_Recommendations.png" width=“275">
   </p>
 - Memory-based approach within Colaborative filtering, with Cosine Similarity technique, when the whole dataset is used directly to find similarities between books, based on rating patterns. Having user to enter a book title, the system recommends those books with highest similarity index
   <p align="center">
   <img src="https://github.com/ValentynaK17/Books-Recommendation-System/blob/main/Output/Book_Based_Recommendation.png" width=“275">
   </p>
 - Model-based methods within Colaborative filtering, with SVD/SVD Funk, used for training and predictions of user rates for books. Having predictions of user rates, for recommendations sytem selects those books, which were not read by user and had highest predicted ratings
   <p align="center">
   <img src="https://github.com/ValentynaK17/Books-Recommendation-System/blob/main/Output/User_Based_Recommendations.png" width=“275">
   </p>

This book recommendation system attempts to suggest books to users based on their past interactions (leaving rating scores for books):
|   | Book1| Book2| ...| BookN|
|----------|----------|----------|----------|----------|
|**User1**| 3 |   |...|8|
|**User2**| 9 | 10|...|8|
|...| ... | ...|...|...|
|**UserN**| 4 | 4|...||


## Installation
1. Assuming Python and Flask are installed, run the app.py script.
2. Access the Web Application by opening a web browser and navigating to the URL generated (e.g. http://127.0.0.1:5000).
   
The home page displays the Most Popular Books, however user can switch to 'Recommend by Book'/'Recommend by User' pages for personalized recommendations. 'Search Book' would help with searching for exact book titles.

### Limitations
This engine uses a static set of data so far.

### Dataset
Our dataset was obtained from [Kaggle](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset). It included these 3 files providing metadata about users and books. We generated a fourth dataset, for further analysis and visualizations.
Books:ISBN, Book title, Book author, Year of publication, Publisher
Users: User ID, Location(country)
Ratings: User ID, ISBN, Book rating
Geo Location: Country, Latitude, Longitude

### Methodology
The project consisted of the following broad steps. Step by step processes are commented within the .ipynb file:
1. Data Preprocessing and cleaning, e.g.
   - convering 'Book-Ratings' as well as 'Year of Publication' to numerical fields;
   - leaving only those records with Year of Publication' >0;
   - handling duplicated records (e.g. use average rate per duplicated records for same userXbook ratings)
   - encoding categorical variables
   - splitting the data into training and testing sets.
2. Exploratory data analysis, e.g.
   - analysis of how many reviews do usually books have
   <p align="center">
   <img src="to add" width=“275">
   </p>
   - analysis of how many books do usually users rate
   <p align="center">
   <img src="to add" width=“275">
   </p>
3. Researching and experimenting on various recommendation system techniques, e.g. 
  - training both SVD and SVD Funk models using the training dataset. To do this the data were devided into training and test sets on a per-user basis. Approximately 80% of each user's records were aassigned to the training set, while the remaining 20% reserved for the test set. This approach helps with having both the training and test sets containing data from all users.
  - taking into account all the data, including implicit ratings VS average mean instead of implicit ratings VS excluding implicit ratings at all
  - cross-validating the model using the Surprise module
  - trying to optimize SVD Funk with hyperparameters tuning (number of latent factors, number of iterations, step size for the gradient descent optimization, regularization term used for all parameter to prevent overfitting)
    
   <p align="center">
   <img src="https://github.com/ValentynaK17/Books-Recommendation-System/blob/main/Output/SVD_Model_RMSE_Comparison_color.png" width=“275">
   </p>
For evaluation of the model RMSE metric was used (Root Mean Square Error)
   <p align="center">
   <img src="to add" width=“275">
   </p>
    where:
    predicted_i is a predicted value for the ith observation and actual_i is an observed(actual) value for the ith observation. N - Total number of observations.
    Accuracy measurement for test set shows that SVD produces a little  inaccurate rating predictions, with tendency to lowering rates. 
We observed that while a tuned SVD Funk improved results, the most accurate predictions emerged from  SVD Funk model with default hyperparameters and weighted mean instead of implicit rating data.
   <p align="center">
   <img src="https://github.com/ValentynaK17/Books-Recommendation-System/blob/main/Output/SVD_Models_RMSE_Comparison_Color_White.png" width=“275">
   </p>

4. Building and interactive website:
    - Flask for handling HTTP requests, manage routing and serving web pages;
    - Pandas for data manipulations
    - Pickle for loadin pre-processed data and a model
    - HTML for areating frontend templates that Flask renders and serves to the client's browser
    - CSS for styling web pages
5. Creation a dashboard visualizations

### Tools, Languages and Libraries
Data Preprocessing and EDA - Python, Jupyter Notebook, Pandas, Matplotlib, Numpy, Scipy, Scikit-learn
Machine Learning - Singular Value Decomposition (SVD), SVD Funk
Web Development - Flask, HTML, CSS
IDE - Visual Studio Code
Visualization - Tableau

### References
 - [Recommendation Engine Concepts](https://www.analyticsvidhya.com/blog/2018/06/comprehensive-guide-recommendation-engine-python/)
 - [BootStrap](https://www.w3schools.com/bootstrap/bootstrap_get_started.asp)  
 - [Flask Documentation](https://flask.palletsprojects.com/en/3.0.x/)  
 - [Jinja Template](https://jinja.palletsprojects.com/en/3.1.x/)  
 - [CSS](https://www.w3schools.com/css/)  


### Acknowledgements
Project Team:
1. Daria Z.
2. Neha S.
3. Seeke O.D
4. Valentyna K.

It has been great working and learning with you all.

 

