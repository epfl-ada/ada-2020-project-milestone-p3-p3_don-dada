## Abstract

The original paper [1] presents a dataset providing food consumption habits according to geographical parameters, and breaks those patterns down to nutrient level. The paper then explores correlations between said habits and health-related issues in the Greater London area, among other explorations. We are proposing to study whether we can analyze and predict other contemporary problems and challenges from this data. Our idea is to expand upon this dataset by linking it to two other factors : COVID-19 related deaths, and Indices of Deprivation (which represent general wealth and well-being in the UK) [2]. We will evaluate the capacity of multiple methods: propensity matching, regression predicting each feature of the meta-dataset based on other features. We will then extract insights from the analysis on potential ways to predict dangerous consumption patterns and areas at risk in the context of the modern pandemic.

[1] Aiello, L.M., Quercia, D., Schifanella, R. et al. Tesco Grocery 1.0, a large-scale dataset of grocery purchases in London. Sci Data 7, 57 (2020).

[2] Payne, Rupert A., and Gary A. Abel. "UK indices of multiple deprivation—a way to make comparisons across constituent countries easier." Health Stat Q 53, no. 22 (2012): 2015-2016.

## Research Questions:
Which pair of features from consumption habits, deprivation, covid-19 deaths are most efficient at predicting the third and under what conditions ?
What are the differences in performance of predictive methods used in interchangeably predictive features in this situation ?


## Proposed Dataset:
All the proposed datasets are for Middle Super Output Areas (MSOA). We want to use the following three datasets to answer our research questions:

**Tesco dataset**: Provides information on the average diet habits in the different areas. Furthermore the dataset provides also important demographic information for the different areas, which could be very important features for the covid-death prediction. The most important features for to answer our research questions are the following:
* energy_fat_x
* energy_sugar_x
* energy_carb_x
* energy_fibre_x
* energy_alcohol_x
* energy_tot_x
* people_per_sq_km_y
* male_y
* female_y
* avg_age_y

**[Covid Deaths](
https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/deaths/datasets/deathsinvolvingcovid19bylocalareaanddeprivation):** We found a dataset on MSOA of all covid deaths in the United Kingdom between March to July. This dataset is the basis for our whole analysis. Since we would like to study the relation between nutrition and covid deaths this dataset is an integral part of our analysis. 


**[Indices of multiple deprivation  (IMD)](
https://research.mysociety.org/sites/imd2019/about/):** We decided to include this dataset because it encapsulates many different demographic informations into one number. The IMD is calculated by considering seven different domains:
* Income. (22.5%)
* Employment. (22.5%)
* Education. (13.5%)
* Health. (13.5%)
* Crime. (9.3%)
* Barriers to Housing and Services. (9.3%)
* Living Environment. (9.3%)

Because it considers so many different aspects of the population it will greatly improve our model. This dataset on MSOA level was derived from the original dataset by the charity MySociety, since the original dataset provided by the Office for National Statistics is only on LSOA level. 

## Methods:
**Propensity score matching:** We decided to use propensity score matching because it provides the best toolset to investigate the causality between nutrition and covid deaths, while excluding all other influences. The “treatment” will be the covid deaths. We will create a binary variable from the covid deaths, depending if the numbers are above and below median. Then we will use one of the two methods below to calculate a propensity score. To evaluate which methods works best, we will first do a unsupervised predictions with a test and train set. We will then take the best method to do the propensity score. Based on this score we match areas. Then we can compare the nutrition for the two groups. 

**Linear & Log Regressions:** As they often prove to be very efficient methods, we decided to train regression models to serve as a baseline for other methods. We will use it to predict the number of covid deaths in the areas based on the features described in the Dataset section. Since it’s supervised learning we need to split the data in train and test data. 

**Boosted decision trees:** Since this method can produce high-quality models we want to use it for our analysis. 


## Proposed timeline
**Week 1:**
* Get datasets
* Merge datasets according to the common areas (MSOA level)
* Compute features, compute covid binary variable in our case
* Familiarize ourself with the data

**Week 2:**
* Split dataset in a training and testing set for Linear & Log Regression and Boosted decision tree
* Train models
* Test models
* Propensity analysis
* Fixing the structure of the datastory

**Week 3:**
* Gather results and create a good visualization of them
* Finishe writing the datastory

Note : if we want to compare multiple models, the preprocessing of the data will change depending on the model.

## Organization within the team

A way to organize the team would be to have one of us doing the data merging and preprocessing, another to split the datasets and train/test the models. The last one would gather the results and do the visualization part. Obviously we will help each other for each part of the milestone. Here, is a list of each task splitted among each student along the timeline
Student 1 :
* Get every dataset
* Merge datasets
* Preprocessing and feature calculation
Student 2:
* Split dataset 
* Train and test models
Student 3:
* Get results and create visualization.

## Questions to TAs:

Is it the right method to create a binary variable from the covid deaths as described in the methods section or should we take another approach?
Is it relevant to compare those two approaches?
