# AI-Trading-Bot

## Disclaimer

This project is for educational purposes only. It is not intended for actual trading or financial advice. The creator of this project takes no responsibility for any financial losses or gains incurred by individuals who use this software. Exercise caution and consult with a financial professional before engaging in any trading activity.

## Introduction

This project is my first large-scale AI endeavor, focusing on the integration of machine learning with financial markets. It combines predictive modeling using LSTM neural networks and real-time data analysis to explore automated trading strategies. Throughout this project, I've learned lessons in model development, data handling, and strategy optimization. I will be exploring other integrations of AI in the future.

## Overview

This project is an AI-powered trading bot designed to automate trading using a Long Short-Term Memory (LSTM) model. The bot leverages financial data retrieved from the Alpaca API to predict stock prices for S&P 500 tickers. The primary goal is to maximize profit through predictive analytics and a robust trading strategy that adapts to market conditions.

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [How to Use](#how-to-use)
- [Data Retrieval](#data-retrieval)
- [LSTM Model](#lstm-model)
- [Trading Strategy](#trading-strategy)
- [Results](#results)
- [Future Work](#future-work)
- [Contributing](#contributing)

## Project Structure

- **Data Retrieval**: Pulls historical and real-time market data from the Alpaca API.
- **LSTM Model**: A neural network architecture specifically tuned for time series prediction, focusing on closing price predictions.
- **Trading Strategy**: Combines machine learning predictions with technical indicators to create dynamic trading rules.

## How to Use

### Prerequisites

Before using the trading bot, ensure you have the following:

- **Python 3.7 or later**: The bot requires Python for running scripts and managing dependencies.
- **Alpaca Account**: Create two accounts on Alpaca and obtain API keys for accessing market data and executing trades. Having two accounts ensures that the bot does not hit rate limits.

### Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/finnjohnston/AI-Trading-Bot.git
   cd AI-Trading-Bot
2. **Install Dependencies:**

   Use 'pip' to install the required Python packages:

   ```pip
   pip install -r requirements.txt
3. **Configure API Keys**

   Create a '.env' file in the root directory and add your Alpaca API credentials

   ```plaintext
   ALPACA_DATA_KEY=your_api_data_key_id
   ALPACA_DATA_SECRET=your_data_secret_key
   ALPACA_TRADING_KEY=your_api_trading_key_id
   ALPACA_TRADING_SECRET=your_trading_secret_key
### Running the Trading Bot

To ensure the AI-powered trading bot operates effectively and makes timely decisions, it must run continuously to retrieve real-time data, make predictions, and execute trades automatically. Continuous execution allows the bot to react promptly to market changes, enhancing its ability to capture profitable opportunities and manage risk dynamically.

- Use an Infinite Loop in Python
- Run as a Background Service
- Employ a Process Manager
- Deploy on Cloud Platforms
  
For detailed instructions on setting up continuous execution, refer to the internet. 

### Workflow 

Here's a step by step explanation of how the trading bot operates:

- Step 1: The bot retrieves historical price data from Alpaca
- Step 2: The LSTM model process the data, making predictions for the next day’s closing prices
- Step 3: The bot calculates technical indicators
- Step 4: Based on predictions, the bot evaluates entry criteria using dynamic thresholds
- Step 5: If entry criteria are met, the bot initiates trades with the specified position sizes
- Step 6: At the end of the trading day, the bot evaluates exit criteria, adjusting to stop-loss and take-profit levels
- Step 7: If exit criteria are met, the bot executes trades to close positions, locking in profits or minimizing losses
- Step 8: The bot updates historical price data
- Step 9: Repeat 2-8 daily

### Troubleshooting

- **Connection Issues**: Ensure your internet connection is stable and your API Keys are correct
- **Model Performance**: If predictions are not accurate, consider tuning hyperparameters

## Data Retrieval

The bot uses the Alpaca API to fetch historical and real-time stock price data

### Key Data Points

- **Historical Prices**: Used for training the LSTM model
- **Real-Time Prices**: Used for making trade decisions based on predictions
- **Technical Indicators**: Calculated features like Moving Averages, Average True Range (ATR), and thresholds

### Data Processing

- **Normalization**: Historical prices are normalized to improve model performance
- **Data Loaders**: Utilized to efficiently manage data batches during training, allowing for streamlined model input handling and reducing memory overhead

## LSTM Model

### Architecture

- **Input Layer**: Takes sequences of historical price data 
- **LSTM Hidden Layers**: Consist of multiple LSTM cells that capture temporal dependencies and patterns
- **Output Layer**: Predicts the next day’s closing price for each ticker

### Training

- **Dataset**: Trained on historical close prices
- **Data Loaders**: Implemented to batch data efficiently during the training process, supporting efficient training workflows
- **Hyperparameters**: Tuned for optimal performance across multiple tickers, including learning rate, batch size, and number of LSTM layers
- **Optimizer**: Adam optimizer is used for its efficiency in handling large datasets and adaptive learning rate capabilities

### Evaluation

- **Validation**: Split data into training and validation sets to avoid overfitting, using k-fold cross-validation for robustness

## Trading Strategy

### Entry Criteria

- **Long positions**: Triggered when predicted prices exceed current prices by a dynamic threshold of 2% of the Moving Average of Returns (MAR)
- **Short positions**: Triggered when predicted prices fall below current prices by a similar dynamic threshold of 2% of the Moving Average of Returns (MAR)

### Exit Criteria

- **Take-Profit and Stop-Loss**: Uses volatility-adjusted metrics based on the Average True Range (ATR) for adaptive risk management
- **Trailing Stops**: Implements trailing stop percentage of 1% that adjusts according to price movements and volatility

### Risk Management

- **Position Sizing**: Trades are sized to risk a fixed percentage of the portfolio on each trade
- **Stop-Loss adjustments**: Stop-loss levels are dynamically adjusted based on ATR to account for changing market conditions

## Results

<img width="743" alt="Screenshot 2024-08-13 at 3 26 08 PM" src="https://github.com/user-attachments/assets/3a64f56b-661a-4825-8460-e43c830b7b7e">


This image showcases a typical trading day where the bot successfully demonstrates positive returns. The steady upward trend in the porfolio value showcases the effectiveness of the predictive model and trading strategy. 


<img width="1153" alt="Screenshot 2024-08-07 at 9 50 32 AM" src="https://github.com/user-attachments/assets/e15dbbd9-a49f-4076-b38e-6415b8462706">


The diverse range of positions managed by the bot demonstrates its ability to efficiently handle multiple assets. The posditive total P/L percentages indicate its proficiency in selecting trades for both long and short positions.


<img width="747" alt="Screenshot 2024-08-06 at 7 56 00 AM" src="https://github.com/user-attachments/assets/87cb5b7e-a151-4cce-af16-e29eef345edc">


The top positions section shows the bot's skill in identifying profitable trades. The gains in asset indicates its efficiency and ability to dynamically adjust to market movements, resulting in majority positive P/L figures.  

## Future Work

- Additional features for the LSTM model to enhance prediction accuracy.
- Optimizing trading strategies using feedback from real-time performance data.
- Expanding the strategy to other indices or asset classes, such as commodities or cryptocurrencies.
- Experimenting with other machine learning models for improved predictive capabilities

## Contributing

Contributions are welcome. Please fork the repository, make changes, and submit a pull request. Open an issue for any feature requests or bug reports.
