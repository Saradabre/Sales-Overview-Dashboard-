# Interactive Sales Performance Dashboard

An enterprise-grade analytics solution built to track regional sales performance, profitability, and volume changes across the United States. This dashboard translates complex time-intelligence metrics into clear, actionable executive insights with a dynamic, user-first interface.

## 📋 Project Requirements
**Dynamic Metric Toggling:** Give users the ability to slice the entire dashboard across three distinct lenses: *Sales*, *Profit*, and *Quantity*.
**Geographical Distribution:** Visualize sales metrics across US states dynamically, updating headers and map visual cues automatically based on selected parameters.
**Time Intelligence Comparative Analysis:** Track Current Year (CY) metrics against Previous Year (PY) metrics to measure Year-over-Year (YOY) growth rates.
**Graceful Handling of Empty Historical States:** Implement a robust logic framework to cleanly display `"No Data"` instead of blank spaces or crashing calculations when comparing data against a baseline year (e.g., 2021).

## 🛠️ Tech Stack
**BI Tool:** Microsoft Power BI Desktop
**Data Modeling:** Star Schema (Fact and Dimension Table design)
**Query Engine:** Power Query (M Language) for data ingestion and cleansing
**Analytics Engine:** Data Analysis Expressions (DAX) for advanced time-intelligence and dynamic UI conditioning

## 💾 Data Source Architecture
The underlying data pipeline uses a relational **Star Schema** to optimize performance and data accuracy:
**Fact Table:** `Sales Data` – Houses core transactional records including revenue, margins, order dates, quantity, and product keys.
**Dimension Tables:** * `Calendar Table` – An explicit, continuous date table providing precise granular control over years, months, and historical offsets. Geographical data points containing `Region`, `State`, and localized operational boundaries.

---

## 🌟 Key Features & Implementation Highlights

### 1. Dynamic Map Context Headers
Traditional dashboards require separate charts for separate metrics. This project leverages a single map visual that updates its title dynamically (e.g., *Sales by State*, *Profit by State*, *Qty by State*) using **DAX conditional string outputs** tied to the user's active slicer button. 

### 2. Typeless Data-Safety Layer (DAX Formatting)
Standard DAX metrics break or hide entirely when text data types encounter numeric operators. This model isolates raw calculations inside variables, formatting the results *after* math validation occurs:
**Growth Indicators:** Incorporates custom `UNICHAR` codes (`▲` / `▼`) to immediately telegraph performance trends.
**Robust Error Prevention:** Seamlessly catches historical data gaps to print `"No Data"` in the matrix rows without breaking column total sums.

## 📊 Visuals Included
**Executive Summary Panel:** Centralized KPI cards for Central, East, South, and West regions.
**Geographical Bubble Map:** Integrated Microsoft Bing/TomTom map visual scaled by dynamic metrics.
**YOY Performance Grid:** A detailed conditional table featuring data bars and arrow indicators for quick scannability.

