# ECE2112-PA4
## ECE BOARD EXAM PROBLEM: Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.
## 1. Create the following data frames based on the format provided:
### a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon.

Step 1: First, we must import the Pandas library since this will be the main tool for data manipulation and analysis.
```py
import pandas as pd
```

Step 2: Then, we load the dataset.
```py
df = pd.read_excel("board2.xlsx")
```

Step 2.1: This step is not important, but can be useful for checking whether the loading was successful.
```py
df

	    Name  Gender             Track       Hometown  Math  Electronics  GEAS  Communication
0    S1    Male   Instrumentation         Luzon       58           89    75             78
1    S2  Female     Communication      Mindanao       52           75    90             52
2    S3  Female   Instrumentation      Mindanao       83           74    77             57
3    S4    Male   Instrumentation       Visayas       65           58    91             68
4    S5    Male     Communication         Luzon       59           86    43             88
5    S6  Female  Microelectronics       Visayas       88           45    86             83
6    S7  Female   Instrumentation         Luzon       66           60    60             48
7    S8    Male   Instrumentation         Luzon       49           81    64             53
8    S9    Male   Instrumentation         Luzon       50           36    63             42
9   S10    Male  Microelectronics      Mindanao       80           84    61             44
10  S11  Female     Communication       Visayas       48           56    48             67
11  S12    Male     Communication       Visayas       89           67    84             64
12  S13  Female  Microelectronics         Luzon       88           35    83             43
13  S14  Female  Microelectronics         Luzon       83           77    89             73
14  S15  Female  Microelectronics      Mindanao       69           41    40             86
15  S16  Female     Communication         Luzon       71           70    87             81
16  S17  Female  Microelectronics      Mindanao       81           79    77             45
17  S18    Male     Communication       Visayas       81           40    81             52
18  S19    Male  Microelectronics         Luzon       79           63    79             71
19  S20  Female     Communication      Mindanao       59           60    62             85
20  S21  Female  Microelectronics       Visayas       83           51    68             72
21  S22  Female     Communication       Visayas       64           39    89             58
22  S23    Male   Instrumentation         Luzon       84           70    74             47
23  S24  Female  Microelectronics       Visayas       85           45    60             41
24  S25    Male     Communication         Luzon       74           91    94             42
25  S26  Female   Instrumentation       Visayas       71           47    83             62
26  S27    Male  Microelectronics       Visayas       70           47    40             86
27  S28    Male     Communication       Visayas       85           53    80             53
28  S29    Male   Instrumentation      Mindanao       73           48    71             62
29  S30    Male   Instrumentation         Luzon       78           81    57             56

```

Step 3: We now can create the Instru DataFrame.
```py
Instru = df[(df["Track"]=="Instrumentation") &
            (df["Hometown"]=="Luzon") &
            (df["Electronics"]>70)][["Name","GEAS","Electronics"]]
```

Step 3.1: Print out the DataFrame to check if it matches the expected output:
```py
Instru

Name  GEAS  Electronics
0    S1    75           89
7    S8    64           81
29  S30    57           81

```
<br>

### b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female.

Step 1: Assuming that we have imported the pandas library, we can proceed to computing the average grade.
```py
df["Average"] = df[["Math","Electronics","GEAS","Communication"]].mean(axis=1)
```
Step 1.1: Printing out the dataframe to check if it was done correctly:
```py
df

    Name  Gender             Track       Hometown  Math  Electronics  GEAS  Communication  Average
0    S1    Male   Instrumentation         Luzon    58           89    75             78    75.00
1    S2  Female     Communication      Mindanao    52           75    90             52    67.25
2    S3  Female   Instrumentation      Mindanao    83           74    77             57    72.75
3    S4    Male   Instrumentation       Visayas    65           58    91             68    70.50
4    S5    Male     Communication         Luzon    59           86    43             88    69.00
5    S6  Female  Microelectronics       Visayas    88           45    86             83    75.50
6    S7  Female   Instrumentation         Luzon    66           60    60             48    58.50
7    S8    Male   Instrumentation         Luzon    49           81    64             53    61.75
8    S9    Male   Instrumentation         Luzon    50           36    63             42    47.75
9   S10    Male  Microelectronics      Mindanao    80           84    61             44    67.25
10  S11  Female     Communication       Visayas    48           56    48             67    54.75
11  S12    Male     Communication       Visayas    89           67    84             64    76.00
12  S13  Female  Microelectronics         Luzon    88           35    83             43    62.25
13  S14  Female  Microelectronics         Luzon    83           77    89             73    80.50
14  S15  Female  Microelectronics      Mindanao    69           41    40             86    59.00
15  S16  Female     Communication         Luzon    71           70    87             81    77.25
16  S17  Female  Microelectronics      Mindanao    81           79    77             45    70.50
17  S18    Male     Communication       Visayas    81           40    81             52    63.50
18  S19    Male  Microelectronics         Luzon    79           63    79             71    73.00
19  S20  Female     Communication      Mindanao    59           60    62             85    66.50
20  S21  Female  Microelectronics       Visayas    83           51    68             72    68.50
21  S22  Female     Communication       Visayas    64           39    89             58    62.50
22  S23    Male   Instrumentation         Luzon    84           70    74             47    68.75
23  S24  Female  Microelectronics       Visayas    85           45    60             41    57.75
24  S25    Male     Communication         Luzon    74           91    94             42    75.25
25  S26  Female   Instrumentation       Visayas    71           47    83             62    65.75
26  S27    Male  Microelectronics       Visayas    70           47    40             86    60.75
27  S28    Male     Communication       Visayas    85           53    80             53    67.75
28  S29    Male   Instrumentation      Mindanao    73           48    71             62    63.50
29  S30    Male   Instrumentation         Luzon    78           81    57             56    68.00
```

Step 2: We can now create the Mindy DataFrame.
```py
Mindy = df[(df["Hometown"]=="Mindanao") &
           (df["Gender"]=="Female") &
           (df["Average"]>=55)][["Name","Track","Electronics","Average"]]
```

Step 2.1: For checking if the expected output was accomplished, we can print out the DataFrame.
```py
Mindy

 Name             Track  Electronics  Average
1    S2     Communication           75    67.25
2    S3   Instrumentation           74    72.75
14  S15  Microelectronics           41    59.00
16  S17  Microelectronics           79    70.50
19  S20     Communication           60    66.50
```

##  2. Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contribute to a higher average score?

Step 1: We will import the Matplotlib library first before we proceed to other steps since it's needed for creating data visualizations.
```py
import matplotlib.pyplot as plt
```

Step 2: First, we'll do the average grade by gender. We will first group the students by gender, calculate the average grade for each gender, and then plot it to a bar chart.
```py
gender_avg = df.groupby("Gender")["Average"].mean()
plt.figure(figsize=(6,5))
plt.bar(gender_avg.index, gender_avg.values, color=["skyblue","pink"])
plt.title("Average Grade by Gender")
plt.xlabel("Gender")
plt.ylabel("Average Grade")
plt.show()

<img width="669" height="581" alt="image" src="https://github.com/user-attachments/assets/b56108f3-0438-4173-89af-4a78cd8b277e" />
```

Step 3: Then, we'll do the average grade by hometown. We will first group the students by their hometown, then calculate the average grade for Luzon, Visayas, and Mindanao. Then lastly, we'll display the results as a bar chart.
```py
home_avg = df.groupby("Hometown")["Average"].mean()
plt.figure(figsize=(6,5))
plt.bar(home_avg.index, home_avg.values, color=["orange","green","blue"])
plt.title("Average Grade by Hometown")
plt.xlabel("Hometown")
plt.ylabel("Average Grade")
plt.show()

<img width="661" height="580" alt="image" src="https://github.com/user-attachments/assets/631555f6-a600-4164-8d22-5f73162efe7d" />
```

Step 4: Then, we'll do average grade by track. We will first group the students by ther track (Instrumentation, Communication, Microelectronics), then calculate their average, and we'll plot the results.
```py
track_avg = df.groupby("Track")["Average"].mean()
plt.figure(figsize=(8,5))
plt.bar(track_avg.index, track_avg.values, color=["steelblue","orange","green"])
plt.title("Average Grade by Track")
plt.xlabel("Track")
plt.ylabel("Average Grade")
plt.xticks(rotation=20)
plt.show()

<img width="859" height="632" alt="image" src="https://github.com/user-attachments/assets/d031f364-ea4b-4959-88a6-5628a2c61deb" />
```

Step 5: Lastly, we will do the average grade by track and gender. We will first group them by their track and gender, calculate the mean average for each subgroup, and plot the results.
```py
group_avg = df.groupby(["Track","Gender"])["Average"].mean().unstack()
group_avg.plot(kind="bar", figsize=(10,6), color=["skyblue","lightcoral"])
plt.title("Average Grades by Track and Gender")
plt.ylabel("Average Grade")
plt.xlabel("Track")
plt.xticks(rotation=20)
plt.legend(title="Gender")
plt.show()

<img width="1054" height="725" alt="image" src="https://github.com/user-attachments/assets/140ba263-b179-48e2-8a05-f10fe4851b3c" />
```
