# Fake-News-Classifier

## Project Description
A fake news classifier is a machine learning model that identifies and flags news articles with false or misleading information. It uses natural language processing to analyze article content and external sources to validate claims. The classifier can filter out fake news and promote fact-based reporting, combating the spread of misinformation.

## Training Dataset
The training dataset was obtained from: https://onlineacademiccommunity.uvic.ca/isot/2022/11/27/fake-news-detection-datasets/
Rename datasets as: "Fake.csv" and "True.csv" 

Acknowledgments: 
  1. Ahmed H, Traore I, Saad S. “Detecting opinion spams and fake news using text classification”, Journal of Security and Privacy, Volume 1, Issue 1, Wiley,           
  January/February 2018.
  2. Ahmed H, Traore I, Saad S. (2017) “Detection of Online Fake News Using N-GramAnalysis and Machine Learning Techniques. In: Traore I., Woungang I., Awad A. (eds)   
  Intelligent, Secure, and Dependable Systems in Distributed and Cloud Environments.ISDDC 2017. Lecture Notes in Computer Science, vol 10618. Springer, Cham (pp. 127- 
  138).
  
## WorkFlow
1. training_data.py - This python file converts the csv files into a pandas dataframe. Dataset is not included in the repository due to its large size.
2. data_processor.py - To take a input data frame and convert the text into a usable format. The input text undergoes several NLP operations like: 1. Expanding Contractions | 2. Remove digits, punctuations, stop words and extra spaces | 3. lemmatize and conversion to a lower case(This case lemmatization first, because news tend to have many proper nouns)
3. models.py - To train a tf-idf vectorizer model and Multinomial NB classification model and store them as a pickle file for later use.
4. fake_news_classifier - Takes the input: Title and Text of the news and uses the model to classify any new news. 
5. frontend.py- Used to make a simple interface for the user to enter the Title and Text of the news and return a prediction.

### Examples:
1) True News(https://therealnews.com/baltimore-comptroller-sidesteps-city-council-to-scrutinize-controversial-tax-break-for-developers)

Title: BALTIMORE COMPTROLLER SIDESTEPS CITY COUNCIL TO SCRUTINIZE CONTROVERSIAL TAX BREAK FOR DEVELOPERS

Text: Taking a major step toward improved public transparency regarding the city’s use of tax incentives to spur development, the Baltimore Finance Board approved a resolution this week that will require the city to post critical data about the costs and benefits of one particularly controversial tax break. Sponsored by Comptroller Bill Henry, the resolution will require the city to produce an annual report aggregating a wide swath of financial information on what are known as TIFs, or tax increment financing deals. TIFs give decades’ worth of future property taxes to developers in advance, the total amount of which is calculated based on projections of how much revenue the new property will generate. The city raises the funds to pay for TIFs by issuing long-term bonds, which the developer pays back using property taxes generated by the new development. This means that, in order to finance a TIF, the city forgoes any new revenue from the property for decades. However, as we have reported on extensively, for all the money the city diverts to developers (and away from the general fund) in the form of tax break instruments like TIFs, the criteria for calculating the size of these tax breaks—and the system for retroactively evaluating whether or not Baltimore and its residents actually benefit from them—are opaque at best (and non-existent at worst). The reporting requirements outlined in Henry’s resolution include the total amount a developer has received from TIF proceeds to build a project, cumulative interest payments for each development, and the total aggregate sum the city has borrowed to finance TIF projects to date. But it also drills down into some details of TIF spending that have otherwise been difficult to obtain. For example, the resolution requires reporting on administrative expenses—such as legal fees and analysis costs—which result from issuing the bonds that finance TIFs. It also includes a side-by-side comparison of how actual spending by developers on the project compares to the original estimates presented when the TIF was approved. 

Output: 

![image](https://user-images.githubusercontent.com/125646791/234464917-20d66165-159e-4723-baf3-30f6a4404452.png)

2) False News(https://www.newyorker.com/humor/borowitz-report/elon-musk-says-rocket-exploded-because-it-insisted-on-working-remotely)

Title: Elon Musk Says Rocket Exploded Because It Insisted on Working Remotely

Text: HAWTHORNE, CA (The Borowitz Report)—One day after SpaceX’s first test flight of its Starship craft, Elon Musk claimed that the rocket exploded in midair because it insisted on working remotely.“Starship was performing perfectly well when it was on the launchpad,” Musk said. “The trouble began when it left.” “I urged Starship against working remotely, but it insisted,” he added. “Well, who was right?” The SpaceX C.E.O. said that Starship’s misadventure should be a lesson to all those employees who insist on working from home. “If you work remotely, you, too, will explode,” he warned.

Output:

![image](https://user-images.githubusercontent.com/125646791/234465387-df0bfdba-1788-4174-be66-9c17cd00e89e.png)

## Model Evaluation Metric Results:
Accuracy: 0.948

Precision Score: 0.947

Recall Score: 0.953

F1 Score: 0.950



