# Midterm Project: Relationship Between Wealth and Coronavirus Deaths

## Project Overview

For this midterm project, I am investigating the relationship between wealth and coronavirus deaths. Specifically, I am analyzing whether regions with lower access to vaccinations tend to have higher death rates and infection rates from COVID-19, and if the primary cause of this shortage is the economic situation of the nation.

### Hypothesis
I hypothesize that nations with lower economic resources (measured by GDP growth) experience higher COVID death rates due to limited access to vaccinations.

### Data Sets
I have gathered three datasets for this project:
1. **GDP Growth (2015)**: Contains GDP growth data for various countries in 2015.
2. **COVID Cases and Deaths (2020-2021)**: Records COVID cases and deaths in different countries during 2020 and 2021.
3. **Vaccination Rates**: Shows the number of people receiving their first, second, and booster vaccinations in different countries.

### Challenges Faced
- I was unable to find recent public data on GDP growth post-2015.
- Some data sets focus only on specific countries or lack population data for comparison.
- The data sets contain extra information not relevant to my analysis.

## Project Structure

### Functions Implemented

1. `def clean_data(data)`: Cleans and processes the data to make it usable.
2. `def convert_to_DoL(data)`: Converts processed data into a Dictionary of Lists (DoL).
3. `def convert_to_LoL(data)`: Converts processed data into a List of Lists (LoL).
4. `def convert_to_DataFrame(data)`: Converts the data structures into Pandas DataFrames.
5. `def comparison_vaccination(data)`: Analyzes the relationship between COVID infection/death rates and vaccination access in different countries.
6. `def comparison_gdp(data)`: Analyzes the relationship between GDP growth and vaccination access in various countries.
7. `def main()`: Coordinates the above functions to conclude whether there is a relationship between COVID cases, deaths, GDP, and vaccination access.

## Data Sources
- **COVID Cases and Deaths Dataset**: covid.csv
- **GDP Growth Dataset**: gdp.csv
- **Vaccination Rates Dataset**: vaccination.csv

## Code Outline

### Data Cleaning and Processing
```python
def clean_data(data):
    # Cleans the dataset to remove unnecessary data or null values
    pass

def convert_to_DoL(data):
    # Converts the dataset into a Dictionary of Lists (DoL)
    pass

def convert_to_LoL(data):
    # Converts the dataset into a List of Lists (LoL)
    pass

def convert_to_DataFrame(data):
    # Converts the dataset into a Pandas DataFrame
    pass
Comparison Functions
python
Copy code
def comparison_vaccination(data1, data2, name1, name2):
    # Compares COVID cases/death rates with vaccination access
    compare = pd.concat([data1, data2], axis=1)
    compare.dropna(inplace=True)
    x = compare[name1]
    y = compare[name2]
    plt.scatter(x, y)
    plt.show()

def comparison_gdp(data1, data2, name):
    # Compares GDP growth with vaccination access
    compare = pd.concat([data1, data2], axis=1)
    compare.dropna(inplace=True)
    x = compare['GDP']
    y = compare[name]
    plt.scatter(x, y)
    plt.show()
Main Function
python
Copy code
def main():
    # Load and clean the datasets
    DoL = convert_to_DoL('covid.csv')
    LoL, columns = convert_to_LoL('gdp.csv')
    df = pd.read_csv('vaccination.csv')

    # Clean and prepare the data
    clean_val = [DoL, LoL, df]
    for value in clean_val:
        value.dropna(inplace=True)

    # Run comparisons
    comparison_gdp(LoL['GDP'], df['people_fully_vaccinated_per_hundred'], 'GDP vs Vaccination')
    comparison_vaccination(DoL['Confirmed'], df['people_fully_vaccinated_per_hundred'], 'Confirmed Cases', 'Vaccination Rate')
Conclusion
By analyzing the relationship between GDP, vaccination rates, and COVID death rates, I hope to uncover whether wealth plays a significant role in access to vaccination and, subsequently, COVID death rates.
