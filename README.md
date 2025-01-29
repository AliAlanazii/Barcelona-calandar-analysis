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
<img width="1013" alt="Screenshot 1446-07-22 at 11 51 57 AM" src="https://github.com/user-attachments/assets/9aff17e9-166f-44f2-b00e-f06b16271884" />

# ✏️ Questions that you might want to address about the given data

## In this code we know hopw much avalaibe and un avaliable room
```python
df.available.value_counts()
```
<img width="1013" alt="Screenshot 1446-07-22 at 11 49 11 AM" src="https://github.com/user-attachments/assets/ed7ef2d1-d8dc-4f36-8b6c-f8629d878ee5" />

* f (false) means not available, t(true) means available.

## We calculate the percentage of avaliable and unavaliable room
```⁠python
avi_per = data['available'].value_counts(normalize = True)*100
avi_per
```
<img width="678" alt="Screenshot 1446-07-22 at 11 53 02 AM" src="https://github.com/user-attachments/assets/b874fa7d-7ffe-44dc-ab99-466865b0a095" />

## Counts for the busiest day!

```python
bus_day = df[df['available']== 'f']['date'].value_counts()
bus_day.head()
```

<img width="678" alt="Screenshot 1446-07-22 at 11 54 50 AM" src="https://github.com/user-attachments/assets/ea97d437-11f1-43d3-a13d-6944dce01a3c" />

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
![image](https://github.com/user-attachments/assets/df8392ae-632b-47be-bc3e-e0892145e484)



































