# Airline Price Analysis | Power BI

An interactive Power BI dashboard project that explores airline ticket pricing patterns and identifies how different factors influence average flight fares.

The project analyses flight prices across airlines, booking timelines, travel classes, departure and arrival times, routes, and number of stops.

## Project Overview

Airline ticket prices can vary significantly depending on the airline, travel class, booking window, departure and arrival times, and selected route.

This project uses flight listing data to explore these variations through interactive dashboards built in Microsoft Power BI.

The objective is to transform raw flight data into meaningful insights that help users understand airline pricing patterns and compare fare differences across different travel conditions.

## Business Questions

The analysis focuses on the following questions:

- How do average ticket prices vary across different airlines?
- How does the number of days before departure affect ticket prices?
- Are tickets booked 1–2 days before departure more expensive than advance bookings?
- How do departure and arrival times influence average fares?
- Which source-destination routes have the highest average ticket prices?
- How significant is the price difference between Economy and Business class?
- How does the number of stops relate to ticket prices?

## Dataset

The project uses a flight pricing dataset containing **300,153 flight listings and 11 columns**.

Key attributes include:

| Column | Description |
|---|---|
| airline | Airline operating the flight |
| flight | Flight identifier |
| source_city | Departure city |
| departure_time | Departure time category |
| stops | Number of stops |
| arrival_time | Arrival time category |
| destination_city | Arrival city |
| class | Travel class (Economy or Business) |
| duration | Flight duration in hours |
| days_left | Days remaining before departure |
| price | Flight ticket price |

## Tools & Technologies

- **Microsoft Power BI** – Dashboard development and data visualization
- **Power Query** – Data cleaning and transformation
- **DAX** – Calculated measures and analytical metrics
- **Excel** – Source dataset

## Data Preparation & Transformation

The dataset was inspected and prepared before dashboard development.

Key preparation steps included:

- Reviewing column names and data types.
- Checking missing values and duplicate records.
- Ensuring numerical fields were assigned appropriate data types.
- Creating a calculated Route field by combining source and destination cities.
- Creating a Booking Category field to classify bookings based on days left before departure.

### Booking Category Logic

| Category | Condition |
|---|---|
| Last-Minute | 1–2 days before departure |
| Advance | 3 or more days before departure |

## Dashboard Overview

The Power BI report consists of three interactive dashboard pages.

### 1. Airline Pricing Overview

Provides a high-level overview of airline pricing patterns.

**Key components:**
- Total Flight Listings
- Average Ticket Price
- Minimum Ticket Price
- Maximum Ticket Price
- Average Flight Duration
- Average Ticket Price by Airline
- Average Ticket Price vs Days Left

### 2. Timing & Route Analysis

Explores how flight timing and route selection relate to ticket prices.

**Key components:**
- Average Ticket Price by Departure Time
- Average Ticket Price by Arrival Time
- Top 10 Routes by Average Ticket Price
- Source City vs Destination City Price Matrix

### 3. Class & Booking Analysis

Examines fare differences across travel classes and booking timelines.

**Key components:**
- Average Ticket Price by Travel Class
- Last-Minute vs Advance Booking Price Comparison
- Last-Minute Price Premium (%)
- Average Ticket Price by Number of Stops

## Key DAX Measures

Some of the measures used in the analysis include:

**Average Ticket Price**
```dax
Average Ticket Price = AVERAGE(Airline_Data[price])
```

**Total Flight Listings**
```dax
Total Flights = COUNTROWS(Airline_Data)
```

**Last-Minute Average Price**
```dax
Last-Minute Avg Price =
CALCULATE(
    [Average Ticket Price],
    Airline_Data[Booking Category] = "Last-Minute (1-2 Days)"
)
```

**Advance Average Price**
```dax
Advance Avg Price =
CALCULATE(
    [Average Ticket Price],
    Airline_Data[Booking Category] = "Advance (3+ Days)"
)
```

**Last-Minute Price Premium**
```dax
Last-Minute Price Premium % =
DIVIDE(
    [Last-Minute Avg Price] - [Advance Avg Price],
    [Advance Avg Price],
    0
)
```

## Interactive Features

The dashboards include interactive slicers and navigation to support exploration of the dataset.

Users can filter the analysis by:
- Airline
- Travel Class
- Source City

The report also includes navigation between dashboard pages for easier exploration.

## Repository Structure

```text
airline-price-analysis-powerbi/
│
├── README.md
├── Assignment.xlsx
└── Airline_Price_Analysis.pbix
```

*Update the PBIX filename above if your actual report uses a different name.*

## How to Explore

1. Clone or download this repository.
2. Open the `.pbix` file using Microsoft Power BI Desktop.
3. Explore the three dashboard pages.
4. Use the available slicers to analyse different airlines, classes, and source cities.

## Project Scope & Limitations

This project focuses on descriptive and exploratory data analysis using historical flight listing data.

It does not implement or train a machine learning model to predict future ticket prices. The term price analysis refers to identifying and visualizing pricing patterns within the available dataset.


**Tools:** Power BI | Power Query | DAX | Excel
