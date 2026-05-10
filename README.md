# COVID-19 Vaccination Analysis

## Project Overview
Analyzed global COVID-19 vaccination data to identify countries with the highest fully vaccinated rates.

## Data Source
- Our World in Data (OWID) COVID-19 vaccination dataset
- 100,000+ records covering 200+ countries

## Tools Used
- Python (Pandas, Matplotlib)
- Google Colab

## Key Insights
| Rank | Country | Vaccination Rate |
|------|---------|------------------|
| 1 | Cuba | 92.5% |
| 2 | Chile | 91.8% |
| 3 | China | 88.1% |
| 4 | South Korea | 87.5% |
| 5 | Spain | 85.3% |

## Visualization
![Chart](chart.png)

## Code
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load data
url = "https://github.com/owid/covid-19-data/raw/master/public/data/vaccinations/vaccinations.csv"
df = pd.read_csv(url)

# Filter latest date and get top 10
latest_date = df['date'].max()
latest = df[df['date'] == latest_date]
top10 = latest[['location', 'people_fully_vaccinated_per_hundred']].dropna().head(10)

# Create chart
plt.figure(figsize=(10, 6))
plt.barh(top10['location'], top10['people_fully_vaccinated_per_hundred'], color='steelblue')
plt.xlabel('Vaccination Rate (%)')
plt.title('Top 10 Countries: COVID-19 Vaccination Rate')
plt.show()
