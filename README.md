# BreakoutAI Internship Project: Options Trading Data Retrieval and Analysis

## Table of Contents
- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Technical Stack](#technical-stack)
- [Functionality](#functionality)
- [Requirements](#requirements)
- [API Integration](#api-integration)
- [Functions Overview](#functions-overview)
- [Data Flow](#data-flow)
- [Usage](#usage)
- [Error Handling](#error-handling)
- [AI Assistance](#ai-assistance)
- [Future Enhancements](#future-enhancements)
- [Conclusion](#conclusion)

## Project Overview
This project is designed to provide a comprehensive tool for retrieving, analyzing, and processing options trading data within the Indian financial markets. 

## Objectives
- To create a Python-based solution for fetching options trading data from the Upstox API.
- To calculate and display key metrics such as margin requirements and premiums for various options.
- To facilitate data filtering and export for further analysis.
- To enhance the understanding of options trading through practical implementation and API usage.

## Technical Stack
- **Programming Language**: Python 3.11
- **Libraries**:
  - `Flask` for creating a web application to handle API requests.
  - `requests` for making HTTP requests to the Upstox API.
  - `pandas` for data manipulation and analysis.
  - `nsepython` for fetching NSE (National Stock Exchange) data.
- **API**: Upstox API for trading data retrieval.

## Functionality
The project includes the following key functionalities:
1. **Data Retrieval**: Fetch option chain data for specified instruments (e.g., NIFTY, BANKNIFTY).
2. **Margin Calculation**: Calculate the required margin for trading options based on user-defined criteria.
3. **Premium Calculation**: Determine the premiums earned for each option based on the highest bid and ask prices.
4. **Data Filtering**: Allow users to filter data based on instrument names, expiry dates, and option types (Call or Put).
5. **Data Export**: Save processed data into CSV files for further analysis and reporting.

## Requirements
Before running the project, ensure you have the following:
- **Python 3.11** or higher installed on your machine.
- Install required libraries using pip:
  ```bash
  pip install Flask requests pandas nsepython
  ```
- Upstox API Credentials: You will need to create an account on Upstox and obtain the API key and secret.

## API Integration
This project leverages the Upstox API for real-time trading data. Key endpoints utilized include:
- **Authentication**: Use OAuth2.0 for secure access to the API.
- **User Profile**: Retrieve user details to check for margin permissions and account status.
- **Options Chain Data**: Fetch live options chain data for specified instruments.

## Functions Overview
1. `get_all_option_chain_data(instruments: list) -> pd.DataFrame`
   - **Purpose**: To fetch and compile option chain data for a list of specified instruments.
   - **Parameters**: `instruments`: A list of instrument names (e.g., ['NIFTY', 'BANKNIFTY']).
   - **Returns**: A DataFrame containing details for both Put Options (PE) and Call Options (CE) across all specified instruments.

2. `fetch_margin_requirement(instrument_name: str, strike_price: float, side: str) -> float`
   - **Purpose**: To simulate and return the margin requirement for a specific option.
   - **Parameters**: `instrument_name`: Name of the instrument (e.g., 'NIFTY'). `strike_price`: The strike price of the option. `side`: Type of option ('CE' for Call, 'PE' for Put).
   - **Returns**: A float representing the margin requirement. Uses placeholder values due to limited margin access.

3. `calculate_margin_and_premium(data: pd.DataFrame) -> pd.DataFrame`
   - **Purpose**: To calculate the margin and premium for each option in the provided DataFrame.
   - **Parameters**: `data`: DataFrame containing options data fetched from the option chain.
   - **Returns**: An updated DataFrame with additional columns for margin and premium.

4. `filter_data_for_example(data: pd.DataFrame, instrument: str, expiry_date: str, sides: list) -> pd.DataFrame`
   - **Purpose**: To filter the DataFrame based on specified criteria for instrument, expiry date, and option types.
   - **Parameters**: `data`: The DataFrame containing options data. `instrument`: The specific instrument to filter by. `expiry_date`: The expiry date to filter options. `sides`: A list indicating option types to include (e.g., ['CE', 'PE']).
   - **Returns**: A filtered DataFrame containing only the relevant options.

## Data Flow
- **Input**: User specifies the instruments and options criteria.
- **Data Retrieval**: The `get_all_option_chain_data` function fetches live data from the Upstox API.
- **Processing**: The fetched data is processed through `calculate_margin_and_premium` to compute relevant metrics.
- **Filtering**: Users can filter results to focus on specific instruments and option types.
- **Output**: Final results can be saved to CSV files for further analysis.

## Usage
### Run the Application:
- Execute the main script to start the application. The application will initiate the authentication process and allow you to fetch data.

### Fetching and Analyzing Data:
- Call the main functions to fetch options data and calculate metrics.
- Example:
```python
instruments = ['NIFTY', 'BANKNIFTY']
option_data = get_all_option_chain_data(instruments)
margin_data = calculate_margin_and_premium(option_data)
filtered_data = filter_data_for_example(margin_data, 'NIFTY', '2024-11-07', ['CE', 'PE'])
```

### Exporting Data:
- Use the `save_to_csv()` method to save the filtered data for offline analysis.

## Error Handling
The code includes error handling for potential issues such as:
- Invalid API responses (e.g., HTTP errors).
- Missing or malformed data.
- User input validation to ensure correct parameters are passed to functions.

## AI Assistance
Throughout the development of this project, AI tools (like ChatGPT) were utilized to:
- Generate code snippets for data retrieval and processing.
- Clarify concepts related to margin requirements and options trading.
- Provide documentation and guidance on API usage and error handling strategies.

## Future Enhancements
- Implement more sophisticated error handling and logging mechanisms for better debugging.
- Explore advanced analytics features such as historical data analysis or predictive modeling.
- Add a user interface for non-technical users to interact with the tool easily.

## Conclusion
This project serves as a comprehensive solution for retrieving and analyzing options trading data in the Indian financial markets. By focusing on data processing, API integration, and user-friendly functionality, it provides valuable insights that can enhance trading strategies and decision-making processes.
