# Barbershop Scheduling Analysis

Exploratory data analysis of a barber's 4 weeks of simulated appointment data, covering visit patterns, service duration, wait times and capacity utilisation, to show where the schedule is over or under-booked.

## Question

**Across four weeks, how does the barber's workload vary by day and time, and where is the schedule over or under-booked?**

It is broken into five sub-questions: demand pattern, service mix and duration, wait times, capacity and idle time, and the trend over the four weeks.

## Data

`barber_appointments.csv` has 237 visits across 24 days (4-30 Aug 2026, no Monday visits). The data is **simulated**, so the findings demonstrate the method and do not describe a real shop.

| Column | Description |
|---|---|
| `date` | Visit date |
| `day_of_week` | Day name |
| `time_block` | Morning (9-12), Afternoon (12-4) or Evening (4-7) |
| `service_type` | Haircut, Haircut + Beard, Beard Trim, Kids Cut, Shave, Colour/Chemical |
| `duration_min` | Service duration in minutes |
| `wait_time_min` | Wait before service in minutes |
| `booking_type` | Walk-in or Appointment |

No client names or clock times are included.

## Method

The notebook follows seven steps: setup, data cleaning and validation, feature engineering, univariate EDA, bivariate EDA, capacity and idle-time analysis, and weekly trend.

Utilisation assumes a 480-minute day and block capacities of 180 (Morning), 240 (Afternoon) and 180 (Evening) minutes. These are assumptions, not values from the data.

## Headline findings

- Saturday has the most visits (52) and Tuesday the fewest (29).
- Average utilisation ranges from 48.1% on Tuesday to 80.7% on Saturday, with 63% overall. Tuesday to Thursday hold 46 of the 71 idle hours.
- By block, Friday evening averages 98% and Tuesday and Wednesday mornings 17%. 10 of 72 day-and-block slots exceeded their capacity, the highest at 133%.
- Mean wait is 6.7 minutes. The longest averages are Saturday and Sunday evenings (9.9 minutes).
- Colour/Chemical has the longest mean duration (60.6 minutes) and Beard Trim the shortest (15.2).
- Weekly visits were 60, 57, 62 and 58.

## Files

- `Barbershop_analysis.ipynb`: the full analysis
- `barber_appointments.csv`: the dataset
- `Barbershop_Analysis_Report.pdf`: written summary of the findings

## Run it

```bash
git clone https://github.com/IsmailEhsann/barbershop-scheduling-analysis.git
cd barbershop-scheduling-analysis
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Barbershop_analysis.ipynb
```

## Limitations

The data is simulated and covers four weeks, so each weekday has only four observations. There are no arrival or start times, so the order of visits within a block cannot be seen. The notebook reports counts and averages only and runs no statistical tests.