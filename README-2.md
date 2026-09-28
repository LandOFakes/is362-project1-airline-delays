# IS 362 Project 1: Airline Arrival Delays

**Author:** Precious Brown  
**Course:** IS 362: Data Acquisition and Management  
**School:** CUNY School of Professional Studies

## Project Overview

This project compares arrival delays for **ALASKA** and **AM WEST** across five destinations using Python and pandas. The analysis compares overall delay rates with destination-specific rates and explains why these comparisons lead to different conclusions.

## Assignment Objectives

1. Create a CSV file containing the flight counts provided in the assignment.
2. Read the CSV into pandas and compare the airlines' arrival delays.
3. Present the code, narrative analysis, and conclusions in a Jupyter Notebook hosted on GitHub.

## Repository Files

| File | Description |
| --- | --- |
| [Precious_Brown_Project1_Airline_Delays.ipynb](Precious_Brown_Project1_Airline_Delays.ipynb) | Notebook containing the code, tables, chart, and narrative discussion. |
| [airline_delays.csv](airline_delays.csv) | Flight counts transcribed from the assignment chart. |
| [requirements.txt](requirements.txt) | Python packages needed to run the notebook locally. |
| [README.md](README.md) | Project overview, setup instructions, methods, and findings. |

## Dataset

The data comes from the **IS 362 Project 1 assignment chart**. It contains 10 observations: one row per airline and destination.

| Column | Description |
| --- | --- |
| `airline` | ALASKA or AM WEST. |
| `destination` | Los Angeles, Phoenix, San Diego, San Francisco, or Seattle. |
| `on_time` | Number of flights arriving on time. |
| `delayed` | Number of delayed arrivals. |

The data contains flight counts, not individual flight records or delay durations.

## Tools Used

- **Python 3** for programming.
- **pandas** for reading, organizing, and analyzing the data.
- **Matplotlib** for the destination comparison chart.
- **IPython** for displaying tables.
- **Jupyter Notebook** or **Google Colab** for running the analysis.

## How to Run

### Google Colab

1. Download `Precious_Brown_Project1_Airline_Delays.ipynb` from this repository.
2. Open [Google Colab](https://colab.research.google.com/).
3. Upload and open the notebook.
4. Run the code cell, or run all cells in order.
5. Review the tables, bar chart, and conclusion.

**Data behavior:** The notebook includes the original data as a CSV string, writes `airline_delays.csv` in the current working directory, and then reads that file with `pd.read_csv()`. No separate CSV upload is required in Colab. Running the notebook overwrites a file with that name in its working directory.

### Local Jupyter Notebook

Download and extract the repository. Open a terminal in the project folder and install the dependencies:

```bash
python -m pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
python -m notebook
```

Open `Precious_Brown_Project1_Airline_Delays.ipynb` and run all cells. GitHub can display the saved notebook, but code execution takes place in Jupyter or Colab.

## Analysis Method

The notebook:

1. Creates and reads the CSV dataset.
2. Calculates total flights, delay percentages, and on-time percentages.
3. Uses `groupby()` to calculate overall airline totals.
4. Uses `pivot()` to compare delay rates by destination.
5. Calculates the difference between the airlines' rates in percentage points.
6. Creates a grouped bar chart of destination-specific delay rates.
7. Calculates each destination's share of an airline's flights.
8. Explains the difference between the overall and destination-specific results.

### Calculations

```python
total_flights = on_time + delayed
delay_pct = delayed / total_flights * 100
on_time_pct = on_time / total_flights * 100
```

Overall delay rates are calculated from total delayed flights divided by total flights for each airline. They are **not** the simple average of the five destination percentages.

## Results

### Overall Comparison

| Airline | On-time flights | Delayed flights | Total flights | Delay rate |
| --- | ---: | ---: | ---: | ---: |
| ALASKA | 3,274 | 501 | 3,775 | 13.27% |
| AM WEST | 6,438 | 787 | 7,225 | 10.89% |

AM WEST has the lower overall delay rate in this dataset.

### Comparison by Destination

| Destination | ALASKA delay rate | AM WEST delay rate |
| --- | ---: | ---: |
| Los Angeles | 11.09% | 14.43% |
| Phoenix | 5.15% | 7.90% |
| San Diego | 8.62% | 14.51% |
| San Francisco | 16.86% | 28.73% |
| Seattle | 14.21% | 23.28% |

ALASKA has the lower delay rate at **every individual destination**.

## Interpretation: Simpson's Paradox

The reversal between the overall and destination-specific comparisons is an example of **Simpson's paradox**.

The airlines have different distributions of flights across destinations. AM WEST has a large share of its flights going to Phoenix, where both airlines have relatively low delay rates. ALASKA has a large share going to Seattle, where both airlines have higher delay rates than in Phoenix. These differences affect the overall weighted rates.

## Conclusion

This analysis demonstrates why it is useful to examine grouped results before drawing conclusions from an overall statistic. AM WEST has the lower overall delay rate, while ALASKA has the lower rate at each destination. Destination-specific rates support comparisons at the same destination; overall rates describe each airline's actual flight mix in this dataset.

## Limitations

- The assignment does not identify the time period covered.
- Delay lengths and causes are not provided.
- The dataset covers only two airlines and five destinations.
- These results describe the supplied data and do not establish the causes of delays or predict future airline performance.
