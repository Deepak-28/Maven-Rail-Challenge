## Maven-Rail_Challenge

## Overview

This Power BI dashboard provides comprehensive insights into train journey data. It includes analysis of the most popular routes, peak travel intervals, revenue from different ticket types and classes, on-time performance, and factors contributing to delays. This tool is designed to help stakeholders make data-driven decisions to enhance operational efficiency and customer satisfaction.

## Features

- **Most Popular Routes**: Identify the most frequented routes based on journey counts.
- **Peak Intervals**: Analyze peak travel times to optimize scheduling.
- **Revenue Analysis**: Breakdown of revenue by ticket type and class.
- **On-Time Performance**: Track punctuality and reliability of train services.
- **Delay Analysis**: Diagnose contributing factors to delays and their impacts.

## Installation

1. **Clone the Repository**
    ```bash
    git clone https://github.com/yourusername/train-journey-dashboard.git
    cd train-journey-dashboard
    ```

2. **Open Power BI Desktop**
    - Ensure you have [Power BI Desktop](https://powerbi.microsoft.com/desktop/) installed.

3. **Load the Dataset**
    - Load your train journey dataset into Power BI.
    - The dataset should include the following columns: `Payment Method`, `Railcard`, `Ticket Class`, `Ticket Type`, `Price`, `Departure Station`, `Arrival Destination`, `Date of Journey`, `Departure Time`, `Arrival Time`, `Actual Arrival Time`, `Journey Status`, `Reason for Delay`, `Refund Request`.

## Usage

1. **Transform Data in Power Query**
    - Open Power Query Editor by clicking on "Transform Data".
    - Select the column `Reason for Delay`.
    - Add a Custom Column with the following formula to replace empty cells:
      ```M
      = if [Reason for Delay] = null or [Reason for Delay] = "" then "No Delay" else [Reason for Delay]
      ```
    - Replace the original column with the new values and rename it if necessary.
    - Apply changes and close Power Query Editor.

2. **Create Calculated Columns and Measures**
    - **Total Revenue**:
      ```DAX
      TotalRevenue = SUM('Table'[Price])
      ```
    - **Delay Duration**:
      ```DAX
      DelayDuration = DATEDIFF('Table'[Arrival Time], 'Table'[Actual Arrival Time], MINUTE)
      ```
    - **On-Time Status**:
      ```DAX
      OnTimeStatus = IF('Table'[Arrival Time] = 'Table'[Actual Arrival Time], "On Time", "Delayed")
      ```

3. **Build Visualizations**
    - **Most Popular Routes**: Stacked Bar Chart showing journey counts per route.
    - **Peak Intervals**: Clusteres Column Chart showing journey counts per hour.
    - **Revenue Analysis**: Slicers for revenue by ticket type and class.
    - **On-Time Performance**: Donut Chart showing on-time vs. delayed journeys.
    - **Delay Analysis**: Slicer showing reasons for delays.

4. **Arrange the Dashboard Layout**
    - Organize visualizations for clarity and usability.
    - Use slicers for interactive filtering (e.g., Date of Journey, Ticket Type).

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or suggestions.

## Contact

For any questions or feedback, please reach out to [yourname@yourdomain.com](mailto:yourname@yourdomain.com).

---

### Screenshots

![Dashboard Screenshot](path/to/screenshot.png)

### Data Source

Ensure that your dataset contains the following columns:
- `Payment Method`
- `Railcard`
- `Ticket Class`
- `Ticket Type`
- `Price`
- `Departure Station`
- `Arrival Destination`
- `Date of Journey`
- `Departure Time`
- `Arrival Time`
- `Actual Arrival Time`
- `Journey Status`
- `Reason for Delay`
- `Refund Request`

---

### Additional Resources

- [Power BI Documentation](https://docs.microsoft.com/en-us/power-bi/)
- [DAX Reference](https://docs.microsoft.com/en-us/dax/)
- [Power Query M Language Specification](https://docs.microsoft.com/en-us/powerquery-m/)

# Maven-Rail-Challenge
