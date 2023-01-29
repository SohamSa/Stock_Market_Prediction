# Stock_Market_Prediction
Stock Market Prediction of Real SNP500 Dataset 

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
