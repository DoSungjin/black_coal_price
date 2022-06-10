# black_coal_price
 
# Purpose 

  When the firm buy blackcoal we want to give imformation about price
  Furthermore we want the stock is managed effectively
  ![image](https://user-images.githubusercontent.com/100894816/172108400-d6088db0-4ace-48b2-9f9c-8aa6be37c200.png)

 
# Procedure

Fist of all, there is a model about price. And then we do backtesting for profit. 
  1. Reference
  2. Data crawling 
  3. EDA
  4. Modeling
  5. Evaluation
  6. Back testing
 
 
# Modeling  
1) arima
 * one-to
 
 - check the data is stationary
 * ![image](https://user-images.githubusercontent.com/100894816/172109848-f395798d-6b2e-46d2-93a0-c5e55502ffed.png)
    (Make ACF, PACF graphs)
    
 * ![image](https://user-images.githubusercontent.com/100894816/172109881-bfa29e23-b8fd-42bb-bb6b-b1b1cec04ec7.png)
    (Make Differenced Data(Stationary)
 - seasonal decomposition
   ![image](https://user-images.githubusercontent.com/100894816/172109745-d112bb03-ca70-4b21-834e-9c984631d0bd.png)
 
 - In sample test
  ![image](https://user-images.githubusercontent.com/100894816/172110201-5cf0ea90-f8aa-4c2c-b03d-8fd3480e849e.png)

 - Out of Sample test
   ![image](https://user-images.githubusercontent.com/100894816/172110231-b53ca516-a985-46c6-b11b-218e6e85f205.png)

 - Parameter optimizing
 - ARIMA SARIMA
 * ![image](https://user-images.githubusercontent.com/100894816/172110466-b60fa05b-32ec-451e-a169-b0729239079e.png)


In sample test, we saw the result is following the true value well. 
But Out of sample test, it follow the trend only.


2) prophet
one-to
- Basic model
  Prophet make well if the data has a Seanality & Trend. Also, if there is a event that we can't expect we can set the event as we know.
  But Blackcoal is a raw materials product that is effected by spply and demand. So I expect the result is poor as long as i do the prophet on blackcoal only.
  As i know, Prophet is good at Supply, Demand and Economic indicators like USD/AUD, S&P. 
  So we will use the prophet as a feature that can predict the blackcoal price.
  
- In sample test
 ![image](https://user-images.githubusercontent.com/100894816/172273744-6d807f15-9131-49e3-8090-db28967cca2a.png)



- Out of Sample test
  - prophet result
  - bdi
  - 
- Prameter chainge

   1.Trend

    **changepoints**	
    **changepoint_prior_scale**	
    **n_changepoints**	
    **changepoint_range**	


   2. Seasonality
   **yearly_seasonality**	
   **weekly_seasonality**	
   **daily_seasonality**	
   **seasonality_prior_scale**	
   **seasonality_mode**	

 
 
 
3) lstm
many-to-many 
 
4) Xgboost
many-to-many
 
5) 1D convolution
many-to-many
