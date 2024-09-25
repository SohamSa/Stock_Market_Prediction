# Stock Market Prediction of Real SNP500 Dataset 

## Project Background and Real Reasoning:

This Stock Market Prediction project was initiated under the guidance of Professor Grace Wang, the Deep Learning Professor and AI Research Head at the New Jersey Institute of Technology (NJIT). The primary objective of this project was to explore how different approaches to executing deep learning projects can impact the financial industry's strategic insights, specifically for NJIT's industry partners.

Financial industry partners often grapple with the challenge of predicting stock market returns, a task traditionally approached using historical data. While it is widely acknowledged that historical data is beneficial for identifying trends and patterns, it does not directly equate to accurate predictions of future returns. This project aimed to bridge that gap by determining which deep learning neural network models are best suited for specific questions related to stock market predictions.

The project's main task was to predict the real S&P500 Index returns using historical data from Yahoo Finance. The approach involved using the previous 20 days' return values as features to predict the 21st day’s return value. The rationale behind this approach was to determine whether applying highly complex neural network models to historical data could provide accurate predictions of future stock market returns, thereby validating their scalability for more sophisticated financial models.

The outcome of the project was not just a demonstration of predictive accuracy but also a proof of concept. If these models, when applied to historical data, could yield highly accurate predictions, they could be expanded and scaled up to include a multitude of factors, making them invaluable for financial industry applications. The findings from this project were utilized by Professor Wang to assist NJIT’s finance industry clients in developing highly sophisticated stock market prediction models.

a. problem statement:
The goal of this project is to predict the real S&P500 Index returns.


b. data set with a link and feature description: 
https://finance.yahoo.com/quote/SPY/history?period1=1482969600&period2=1640131200&interval=1d&filter=history&frequency=1d&includeAdjustedClose=true
Previous 20 days’ return values were used as features to predict the 21st day’s return value.

c. your model and hyperparameters. how long it takes for you to train the model:
TCN. It takes about 2-3 minutes to train this model. Input_shape is (TimeSteps,1), where TimeSteps is the number of days used to predict the next return. We set it as 20.

 **model = Sequential()
 model.add(Conv1D(filters=64, kernel_size=3, activation='relu', input_shape=(TimeSteps,1)))
 model.add(Conv1D(filters=32, kernel_size=3, activation='relu'))
 model.add(Dropout(0.2))
 model.add(MaxPooling1D(pool_size=2))
 model.add(Flatten())
 model.add(Dense(50, activation='relu'))
 model.add(Dense(1))
 model.compile(loss='mean_squared_error', optimizer='adam')**

 **model.fit(X_train,Y_train,validation_data=(X_test,Y_test),verbose=2,epochs=1000)** 
  

d. baseline, metrics, and performance evaluation:
Baseline models: SimpleRNN, LSTM, GRU
Metrics used to evaluate the models: RMSE

## Results:

Prediction Based on the Previous N=20 Days (Model: TCN):
predicted_Return = model.predict(LastNDays)
predicted_Return

Output:
array([[0.00064314]], dtype=float32)

## Conclusion:
The best performance was achieved by the Temporal Convolutional Network (TCN) with RMSE values of 0.004 for the training set and 0.009 for the test set. The predicted return for December 13 was 0.00064314.

## Project Insights and Impacts:
The project's results demonstrated that advanced neural network models, such as the Temporal Convolutional Network, are highly effective in predicting stock market returns when trained on historical data. The TCN model outperformed traditional models like SimpleRNN, LSTM, and GRU, providing significantly lower RMSE values, which indicates a higher prediction accuracy.

These findings were particularly valuable as they offered NJIT’s finance industry clients new methodologies to enhance their existing financial models. By applying complex neural network models, clients could refine their predictive capabilities, enabling more accurate and reliable stock market forecasts. The project underscored the importance of selecting the right model for specific prediction tasks and illustrated how academic research can directly influence real-world financial strategies.

The success of this project lies in its potential for scalability, demonstrating that what began as a classroom project could evolve into sophisticated tools capable of influencing financial decision-making on a much larger scale.
