# algo-trading-backtester

The goal of this project was to implement machine learning models and backtesting algorithms in a Google Colab notebook to find the optimal algorithmic trading strategy between a machine learning model and a simple moving average (SMA) crossover strategy for any stock or crypto asset. We first determined the optimal SMA window pairs that would provide the highest net profit and/or Sharpe ratio for a SMA crossover algorithmic trading strategy by backtesting a variety of moving average window pairs using Gridsearch from sci-kit learn. We then compared the results of this backtest to a machine learning SVM model to see which outperformed the other, if any.

## Technologies

This project leverages Python 3.7 in Google Colab with the following libraries:
- pystan
- fbprophet
- hvplot
- holoviews
- fastquant
- streamlit
- sklearn
- pandas
- numpy
- matplotlib

## Installation Guide

To use this notebook, open the Google Colab notebook and run the notebook. The required installations should be listed in the first cell of the notebook. Simply run the cell to install the required libraries.

## Usage

This notebook allows for various user customizations pertaining to the asset of choice and the time period to run the backtest analysis. If you would like to customize these features, feel free to adjust the arguments in the first cell after the import.

The original line of code is listed as:

```
ticker = 'TSLA'
start_date = '2018-01-01'
end_date = '2021-12-31'
```

Users may choose any stock or crypto under "ticker" as well as any time period for the start and end dates. The date format must be in YYYY-MM-DD. To choose a crypto, the function get_stock_data() must be replaced with get_crypto_data().

In order to change the moving average window periods to be tested, users can edit the range in the following line of code:

```
fast_periods = np.arange(1,21,2, dtype=int)
slow_periods = np.arange(10,200,10, dtype=int)
```

The first number is the start of the range, the second number is the end of the range, and the third number is the number of integers to skip in the gridsearch. In this example, the fast period is a range from 1 to 21 and skips every 2 numbers.

Once the customizations are complete, run the cells in order to view the results.


## Summary Results 
After using GridSearch and Fastquant, we were able to find the optimal Trading Window for our SMAC algo with TSLA stock. We then created an SVM model using the same closing pricing data which, unfortunatly, performed worse than the standard SMAC trading strategy.  Lastly, we created a Logistic Regression model which performed better than the SVM model and inline with the SMAC optimal trading windows.  

The SVM Model produced the following results:

![image](https://user-images.githubusercontent.com/89708427/149682400-b4248dab-9235-479a-91e4-867d786a5d93.png)

![image](https://user-images.githubusercontent.com/89708427/149682428-986aca44-b293-4e6e-bb8c-de2d85bdb3cb.png)

The Logisitic Regression model resulted in an accuracy of 0.578:

![image](https://user-images.githubusercontent.com/89708427/149682457-ed4bdcd8-ef7e-4282-9e47-5247c54acdc9.png)

Using GridSearch to find the best trading window, the follwing Heatmap was produced: 

![image](https://user-images.githubusercontent.com/89708427/149682484-fe447428-b34d-484c-a5f9-1c10b4584851.png)

The following Sharpe Ratio Heatmap was produced with the range of trading Window combinations:

![image](https://user-images.githubusercontent.com/89708427/149682611-edb85771-8b0a-4718-8cca-2a2e6e575cdc.png)


Using the optimal Trading Window, the algo performance vs the actual stock performance was captured here: 

![image](https://user-images.githubusercontent.com/89708427/149682562-3ea2d446-3de3-4818-9175-061b4244f13b.png)

## Google Colab

In the instance one would like to access the project via Google Colab and the project cannot be viewed in this Repository, please use the following link: https://colab.research.google.com/drive/1N6bBfsWvvmnC4eSdUBjZxEiiTKTv5gKb?authuser=2#scrollTo=UcwXodioqwZK 

## Contributors
Austin Do (austindotech@gmail.com), Nev Douglas, Kanika Sharma (ksharmaconnect3@gmail.com), Jason Muenzen (jmuenzen@gmail.com), Max Gregory (maximillian.gregory@gmail.com)


## License

MIT
