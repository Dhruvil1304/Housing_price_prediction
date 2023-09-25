# First Project: House Rental Price Prediction

#### Prepared by: Dhruvil Modi

This is the first predictive analytics project to fulfill the submission requirements for Dicoding. This project aims to build a machine learning model that can predict house and apartment rental prices in India.

## Project Domain

### Background

Housing, such as houses or apartments, is a primary need for humans to shelter and live in. The value of a dwelling depends on its characteristics, such as location, size, number of rooms, number of bathrooms, furnishings, and other features.

![House](https://user-images.githubusercontent.com/107544829/190916847-d1c452eb-7fc4-44a5-b716-4906f4f81de3.png)

[Image Source](https://wallpapersafari.com/w/bdae9M)

The price of each house is determined by its characteristics. However, this price is not always certain and is difficult to predict accurately manually. To reduce uncertainty, rental companies can build a predictive system that determines a reasonable rental price for specific property characteristics.

To achieve this, research is conducted to predict house rental prices using machine learning models. The goal is for the model to predict rental prices in line with the market price. This prediction will serve as a reference for companies to rent houses at a price that can generate profits.

Reference: [Analysis of House Price Prediction Based on Specifications Using Multiple Linear Regression](https://ejournal.upnvj.ac.id/index.php/informatik/article/download/3635/1498)

## Business Understanding

This project is designed for a company with the following business characteristics:

+ The company owns or purchases houses and apartments and rents them to consumers.
+ The company offers consulting services on house and apartment rental prices to consumers.

### Problem Statement

1. Which features have the most influence on house or apartment rental prices?
2. How can data be processed to be effectively trained by the model?
3. What is the market rental price for houses based on specific characteristics?

### Goals

1. Identify the most influential features on house or apartment rental prices.
2. Prepare the data for effective model training.
3. Build a machine learning model that can predict house rental prices as accurately as possible based on specific characteristics.

### Solution Statement

1. Analyze the data by performing univariate and multivariate analyses. Understanding the data can also be achieved through visualization. Understanding the data helps determine correlations between features and detect outliers.
2. Prepare the data for modeling purposes.
3. Perform hyperparameter tuning using grid search and build a regression model capable of predicting continuous values. The algorithms used in this project are K-Nearest Neighbors, Random Forest, and AdaBoost.

## Data Understanding & Removing Outliers

The dataset used in this project is a dataset of house rental prices with various characteristics in India. The dataset can be downloaded from [Kaggle: House Rent Prediction Dataset](https://www.kaggle.com/datasets/iamsouravbanerjee/house-rent-prediction-dataset).

Here is some information about the dataset:

+ The dataset is in CSV (Comma-Separated Values) format.
+ The dataset has 4746 samples with 12 features.
+ The dataset has 4 features of type int64 and 8 features of type object.
+ There are no missing values in the dataset.

### Variables in the Dataset

+ Posted On: The date when the data was posted.
+ BHK: The number of bedrooms, living rooms, and kitchens.
+ Rent: The rental price of the house/apartment.
+ Size: The size of the house/apartment in square feet (sqft).
+ Floor: The location and number of floors of the house/apartment.
+ Area Type: The size of the house categorized as Super Area, Carpet Area, or Built Area.
+ Area Locality: The location of the house/apartment.
+ City: The city where the house/apartment is located.
+ Furnishing Status: The status of the house/apartment furnishings, either Furnished, Semi-Furnished, or Unfurnished.
+ Tenant Preferred: The preferred type of tenant according to the owner or agent.
+ Bathroom: The number of bathrooms.
+ Point of Contact: The contact to inquire for more information about the house/apartment.

Of the 12 features, it can be observed that the Point of Contact and Posted On features do not influence house rental prices and will be removed. This is because these two features are not needed in building the rental price prediction model.

### Univariate Analysis

Univariate Analysis involves analyzing each feature separately.

#### Analysis of the number of unique values in each categorical feature

The categorical features City, Furnishing Status, and Tenant Preferred have a relatively even distribution of samples.
![City Distribution](https://user-images.githubusercontent.com/107544829/188319357-fc12fffa-b709-4584-8363-778bc678b328.png)
![Furnishing Status Distribution](https://user-images.githubusercontent.com/107544829/188319651-02ddb783-da3d-41ed-9b5f-9525aaaf9ed1.png)
![Tenant Preferred Distribution](https://user-images.githubusercontent.com/107544829/188319750-1f080942-7826-4eaf-a021-8b9f938a861a.png)

The following features have uneven sample distributions:

+ Area Type
  ![Area Type Distribution](https://user-images.githubusercontent.com/107544829/188318629-f474b626-a16a-4971-ab42-2c183d22b744.png)
  There are only 2 samples of Built Area in the Area Type feature. To avoid high-dimensional data, these two samples will be removed.

+ Floor and Area Locality
  ![Floor Distribution](https://user-images.githubusercontent.com/107544829/188319871-603b24b8-26b2-449b-b42e-59501a4803a7.png)
  ![Area Locality Distribution](https://user-images.githubusercontent.com/107544829/188319880-3226bd04-920e-4050-b5ab-38dec02fc524