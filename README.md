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

# In this code we know hopw much avalaibe and un avaliable room
```python
df.available.value_counts()
```
<img width="1013" alt="Screenshot 1446-07-22 at 11 49 11 AM" src="https://github.com/user-attachments/assets/ed7ef2d1-d8dc-4f36-8b6c-f8629d878ee5" />

* f (false) means not available, t(true) means available.

# We calculate the percentage of avaliable and unavaliable room
```⁠python
avi_per = data['available'].value_counts(normalize = True)*100
avi_per
```
<img width="678" alt="Screenshot 1446-07-22 at 11 53 02 AM" src="https://github.com/user-attachments/assets/b874fa7d-7ffe-44dc-ab99-466865b0a095" />

# Counts for the busiest day!

```python
bus_day = df[df['available']== 'f']['date'].value_counts()
bus_day.head()
```

<img width="678" alt="Screenshot 1446-07-22 at 11 54 50 AM" src="https://github.com/user-attachments/assets/ea97d437-11f1-43d3-a13d-6944dce01a3c" />

#  📈 Plot a bar graph to show availability percentage

