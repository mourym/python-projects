Atliq Hotel data analytics project

In this project I am able to analyse the hotel data and analyzed Bookings and revenue generated per city

bookings made as per the booking platform

<img width="506" alt="image" src="https://github.com/user-attachments/assets/bf6c0aa1-cabf-4eee-ba91-97c60c7a1438">

analyzed the data using describe which give all the stats related the numeric columns present in the data

<img width="554" alt="image" src="https://github.com/user-attachments/assets/f462c753-0982-44a8-abfb-350528301e6c">

Explored the bookings made and found unique properties using groupby function and found out the days on which 
more bookings are made and which bookings are greater than capacity

Data cleaning done based such as removing negative values, in the data we had negative no of guests
so we need to filter guests less than 0 and remove them from the data


Outliers removal using mean, standard deviation methods

df_bookings.revenue_generated.mean(), df_bookings.revenue_generated.median()

avg, std = df_bookings.revenue_generated.mean(), df_bookings.revenue_generated.std()

higher_limit = avg + 3*std
higher_limit

lower_limit = avg - 3*std
lower_limit


df_bookings[df_bookings.revenue_generated>higher_limit]

df_bookings = df_bookings[df_bookings.revenue_generated<=higher_limit]
df_bookings.shape

higher_limit = df_bookings.revenue_realized.mean() + 3*df_bookings.revenue_realized.std()
higher_limit

df_bookings[df_bookings.revenue_realized>higher_limit]

finding columns that have null values. Filled these null values with appropriate subtitute (possible ways is to use mean or median)

df_agg_bookings['occ_pct'] = df_agg_bookings.apply(lambda row: row['successful_bookings']/row['capacity'], axis=1)

new_col = df_agg_bookings.apply(lambda row: row['successful_bookings']/row['capacity'], axis=1)
df_agg_bookings = df_agg_bookings.assign(occ_pct=new_col.values)
df_agg_bookings.head(3)

df_agg_bookings['occ_pct'] = df_agg_bookings['occ_pct'].apply(lambda x: round(x*100, 2))
df_agg_bookings.head(3)

performed data transormations techniques such Creating new columns , Normalization, Merging data, Aggregation

df_agg_bookings.groupby("room_category")["occ_pct"].mean()

df = pd.merge(df_agg_bookings, df_rooms, left_on="room_category", right_on="room_id")
df.head(4)

more booking made on weekends or weekdays

df_june_22.groupby('city')['occ_pct'].mean().round(2).sort_values(ascending=False).plot(kind="bar")

Appended the data using concat function if any new data comes

calculated Reveneu per city

calculated revenue per hotel type, average rating per city, per booking platform























