---
title:  "Getting back into NumPy, Day 2"
date:   2019-04-02 21:49:09 +0200
categories:
  - Programming
tags:
  - NumPy
  - Python
---

Short of time today, so just a small step forward. Yesterday I made the groundwork for the upcoming time series analysis. I imported the data from a CSV file into pandas and made a simple plot of the mean number of keystrokes for every minute of the day.

Today's goal is to make a heat map. It should show the number of keystrokes for every minute of the day, shown for every day since I started logging. This is inspired by the visualizations listed on the github repository for Minute.

Quite early I ran into a problem. Since I’m going to use imshow to show the heatmap, I need a matrix. The matrix needs to have n rows, where n is the number of days, and 1440 columns, one for every minute of the day. But, well, my first log entry isn’t at 00:00:00 on the first day, and my last entry isn’t at 23:59:00 on the last day.

This is where the upsampling procedure I introduced yesterday pays off. I just need to add an entry for 00:00:00 on the first day, and 23:59:00 of the last day, and let Pandas do the rest. The code for this is as follows:

{% highlight python %}
# Make sure first minute of first day and last minute of last day is included
min_date = df.index[0]
max_date = df.index[-1]
min_date_beginning = datetime.datetime(min_date.year, min_date.month, min_date.day, 0, 0, 0, 0)
max_date_end = datetime.datetime(max_date.year, max_date.month, max_date.day, 23, 59, 0, 0)
df.at[min_date_beginning, 'strokes'] = 0
df.at[max_date_end, 'strokes'] = 0
upsample = pd.DataFrame()
upsample = df.resample('min').asfreq().fillna(0)
upsample.index = pd.to_datetime(upsample.index)
{% endhighlight %}

Now we have a complete set of rows with 1440 entries.

The heat map code I borrowed from the article Time Series Data Visualization with Python from Machinelearningmastery.com. It’s straightforward and it uses the groupby functionality. Introducing a small helper function, we can first group the entries by the day from the first logging date and then add them in a matrix that we give as input to imshow. Changing to a nice heatmap gives a nice color.

The full code for this is as follows (the function datetime_to_minute_of_day I introduced yesterday):

{% highlight python %}
def datetime_to_minute_of_day (datetime):
    return 60*datetime.hour + datetime.minute
def days_from_first_loggingdate (datetime):
    timedelta = datetime - min_date_beginning
    return timedelta.days

# Heatmap over all days
groups = upsample.groupby(lambda x: days_from_first_loggingdate(x))
days_so_far = pd.DataFrame()
for name, group in groups:
    days_so_far[name] = group['strokes'].groupby(lambda x: datetime_to_minute_of_day(x)).sum().values
plt.imshow(np.transpose(days_so_far), interpolation=None, aspect='auto', cmap="hot")
plt.title("Distribution of keystrokes from starting day")
plt.xlabel("Minute of day")
plt.ylabel("Day from log start")
plt.colorbar()
plt.show()
{% endhighlight %}

This yields a nice heatmap, showing how little I actually use my laptop! :-D

![Heatmap of keystrokes from log starting day. Brighter means more keystrokes.](/assets/blogpost_images/2019-04-02_keystrokes.png)