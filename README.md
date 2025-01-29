# 🧑‍💻 Barcelona calandar analysis
Barcelona Calendar Analysis provides insights into event trends, schedules, and patterns in Barcelona over time.

# 🌐 For the following analysis we download the real air bnb data from:
* https://insideairbnb.com/get-the-data/
* All calculations have been performed based on real data from Barcelona.
* <img src="https://github.com/user-attachments/assets/18485c34-5b87-4ddd-a1e4-3a936d43c2ca" alt="Value Counts Output" width="600"/>

## 🌐 Download calendar dataset of Barcelona from:
https://data.insideairbnb.com/spain/catalonia/barcelona/2024-09-06/data/calendar.csv.gz


* After landing on the website you can click on calendar.csv.gz and it will be downloaded!
* If you are using Google Collab then .gz will give you no issues

```python
import pandas as pd
df = pd.read.csv('calender.csv')

```
<img width="1013" alt="Screenshot 1446-07-22 at 11 51 57 AM" src="https://github.com/user-attachments/assets/18eb0de9-23c2-40d9-ba41-bd1a54ddb6ec" />

# ✏️ Questions that you might want to address about the given data

## In this code we know hopw much avalaibe and un avaliable room
```python
df.available.value_counts()
```
<img width="1013" alt="Screenshot 1446-07-22 at 11 49 11 AM" src="https://github.com/user-attachments/assets/2fe58ae8-88e5-4467-add9-b45c54bbd2e3" />

* f (false) means not available, t(true) means available.

## We calculate the percentage of avaliable and unavaliable room
```⁠python
avi_per = df['available'].value_counts(normalize = True)*100
avi_per
```
<img width="678" alt="Screenshot 1446-07-22 at 11 53 02 AM" src="https://github.com/user-attachments/assets/358a6c93-957b-4259-9fa7-88d23e2e623a" />

* f (false) means not available, t(true) means available.

## Counts for the busiest day!

```python
bus_day = df[df['available']== 'f']['date'].value_counts()
bus_day.head()
```

<img width="678" alt="Screenshot 1446-07-22 at 11 54 50 AM" src="https://github.com/user-attachments/assets/cd8c6d83-ad30-4e92-b79a-a435956faeec" />

##  📈 Plot a bar graph to show availability percentage
```python
import matplotlib.pyplot as plt
avi_per.plot(kind='bar', color=['blue', 'pink'])
plt.title('Availability Percentages')
plt.ylabel('Percentage')
plt.xlabel('Available (t/f)')
plt.show()
````

<img src="https://github.com/user-attachments/assets/e480c43f-b952-4ad6-b801-cd0eea17eb65" alt="Value Counts Output" width="600"/>

## 📈 Plot the busiest day

```python
bus_day.head(10).plot(kind='bar', color='lightblue')
plt.title('Top 10 Busiest Dates')
plt.ylabel('Number of Listings Unavailable')
plt.xlabel('Date')
plt.show()
```

<img src="https://github.com/user-attachments/assets/79a89434-b93f-4d71-a977-a187f0717295" alt="Value Counts Output" width="600"/>

# 🌐 Download listings dataset of Barcelona from :
https://data.insideairbnb.com/spain/catalonia/barcelona/2024-09-06/visualisations/listings.csv

```python
import pandas as pd
listings = pd.read_csv('listings.csv')
```
<img src="https://github.com/user-attachments/assets/7684d594-09c3-418c-b580-45216bc4f17d" alt="Value Counts Output" width="600"/>

```python
listings.columns
```
<img src="https://github.com/user-attachments/assets/be7a29d3-4d39-4e76-bf02-15446ab07cb1" alt="Value Counts Output" width="600"/>


## 💸 Room type and price is given seperately
```python
import matplotlib.pyplot as plt
price_by_room = listings.groupby('room_type')['price'].mean()
print(price_by_room)

# Plot price by room type
price_by_room.plot(kind='bar', color='red')
plt.title('Average Price by Room Type')
plt.ylabel('Average Price')
plt.xlabel('Room Type')

plt.show()
```
<img src="https://github.com/user-attachments/assets/df8392ae-632b-47be-bc3e-e0892145e484" alt="Value Counts Output" width="600"/>

## 📈 Top 10 neighborhoods with the most listings
```python
neighborhood_counts = listings['neighbourhood'].value_counts().head(10)
print("Top 10 Neighborhoods by Listings:")
print(neighborhood_counts)

# Plot neighborhoods with most listings
neighborhood_counts.plot(kind='bar', color='lightcoral')
plt.title('Top 10 Neighborhoods by Listings')
plt.ylabel('Number of Listings')
plt.xlabel('Neighborhood')
plt.xticks(rotation=90)
plt.show()
```
<img src="https://github.com/user-attachments/assets/97a35547-08fb-4253-8a6e-36fd04094e01" alt="Value Counts Output" width="600"/>
<img src="https://github.com/user-attachments/assets/f239e275-67f0-4dbe-bed1-0eaffc5107b0" alt="Value Counts Output" width="600"/>

## 📈 Geographical Distribution of Listings (💸 Price Colored)
```python
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10, 6))
sns.scatterplot(data=listings, x='longitude', y='latitude', hue='price', palette='viridis', size='price', sizes=(10, 200))
plt.title('Geographical Distribution of Listings (Price Colored)')
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.show()
```
<img src="https://github.com/user-attachments/assets/146496b2-6f02-483c-ac31-88c6bfebb053" alt="Value Counts Output" width="600"/>

## 📌 Let us see the listings on a real map
#### Hotter Areas (Red/Yellow) in Barcelona:
* High Density:
Areas highlighted in red or yellow (the "hot" colors) indicate a higher concentration of listings. This means there are many available rental properties in these parts of the city.
* Popular Locations:
These regions are likely in high demand, often near major attractions such as La Rambla, Sagrada Família, the Gothic Quarter, or Barceloneta Beach. These are the areas where tourists and visitors tend to stay the most.
#### Colder Areas (Green/Blue) in Barcelona:
* Low Density:
The blue or green (the "cold" colors) indicate a lower concentration of listings, meaning fewer rental properties are available in these zones.
* Less Popular Locations:
These areas might be farther from the main tourist hotspots, often located in quieter residential neighborhoods like Horta-Guinardó or Sant Andreu. Lower density could also suggest more affordable stays due to less competition.
#### Density Patterns in Barcelona:
* Clustered Areas:
If you see clusters of heatmap intensity, these hotspots likely correspond to busy locations such as Passeig de Gràcia, Plaça de Catalunya, or areas near Camp Nou, where visitor activity is high.
* Spread-Out Listings:
A more even spread of listings across Barcelona could indicate that demand is balanced, with travelers booking stays across different neighborhoods rather than just the central areas.

```python
import folium
from folium.plugins import HeatMap
import pandas as pd


Barcelona_data = listings[['latitude', 'longitude', 'price']]  # Example, you may add more columns

# Create a base map centered around Hawaii
a = folium.Map(location=[41.403763895076544, 2.2017716019349334], zoom_start=10)

# Prepare the data for the heatmap
heat_data = [[row['latitude'], row['longitude']] for index, row in Barcelona_data.iterrows()]

# Add the heatmap to the map
HeatMap(heat_data).add_to(a)

# Save the map as an HTML file to view in a browser
a.save('Barcelona_heatmap.html')

# If you're using Jupyter Notebook, you can display the map directly in the notebook:
a
```
<img src="https://github.com/user-attachments/assets/2f3b767f-4342-4541-a74f-150faaf19c35" alt="Value Counts Output" width="600"/>

## 📌 🚨 How do I find location for my city?
* Type your city name on Google Maps
* Right click
<img src="https://github.com/user-attachments/assets/c5fe1d69-030e-49c4-8410-75c6cd67ac5b" alt="Value Counts Output" width="600"/>

## 🔍️ Question 1: What is the proportion of listings with more than 100 reviews?
```python
# Count listings with more than 100 reviews
highly_reviewed_listings_count = listings[listings["number_of_reviews"] > 100].shape[0]

# Plot the result
plt.figure(figsize=(6, 6))
labels = ["Listings with >100 Reviews", "Other Listings"]
sizes = [highly_reviewed_listings_count, listings.shape[0] - highly_reviewed_listings_count]
colors = ["lightcoral", "lightgray"]
plt.pie(sizes, labels=labels, autopct="%1.1f%%", colors=colors, startangle=140, wedgeprops={"edgecolor": "black"})

plt.title("Proportion of Listings with More than 100 Reviews", fontsize=14)

# Show the plot
plt.show()
```
<img src="https://github.com/user-attachments/assets/48d0648e-cb2d-406f-ae91-7b97cf96974f" alt="Value Counts Output" width="600"/>

## 🔍️ Question 2: Find the top 10 neighbourhoods with the most listings available all year (365 days)
```python
# Find the top 10 neighbourhoods with the most listings available all year (365 days)
top_neighbourhoods_availability = listings[listings["availability_365"] == 365]["neighbourhood"].value_counts().head(10)

# Plot the result
plt.figure(figsize=(8, 5))
top_neighbourhoods_availability.plot(kind="bar", color="lightpink", edgecolor="black")

plt.title("Top 5 Neighbourhoods with Listings Available All Year", fontsize=14)
plt.xlabel("Neighbourhood", fontsize=12)
plt.ylabel("Number of Listings", fontsize=12)
plt.xticks(rotation=45, ha="right")
plt.grid(axis="y", linestyle="--", alpha=0.7)

# Show the plot
plt.show()
```
<img src="https://github.com/user-attachments/assets/dac3bc85-6d48-4237-900c-c52ba798e6cc" alt="Value Counts Output" width="600"/>













































