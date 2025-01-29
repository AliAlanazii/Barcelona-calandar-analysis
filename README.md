# Barcelona calandar analysis
Barcelona Calendar Analysis provides insights into event trends, schedules, and patterns in Barcelona over time.
## 🌐 For the following analysis we download the real air bnb data from:
https://data.insideairbnb.com/spain/catalonia/barcelona/2024-09-06/data/calendar.csv.gz

<img src="https://github.com/user-attachments/assets/18485c34-5b87-4ddd-a1e4-3a936d43c2ca" alt="Value Counts Output" width="600"/>

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

# 📈 Top 10 neighborhoods with the most listings
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





































