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
  Prophet make well if the data has a Seanality & Trend. 
  Also, if there is a event that we can't expect we can set the event as we know.
  But Blackcoal is a raw materials product that is effected by spply and demand. 
  So I expect the result is poor as long as i do the prophet on blackcoal only.
  As we know, Prophet is good at Supply, Demand and Economic indicators like USD/AUD, S&P. 
  So we will use the prophet as a feature that can predict the blackcoal price.
  
- Equation of Prophet 
  y(t) = g(t) + s(t) + h(t) +et
  -g(t) = Trend that has not repetitive elements
  -s(t) = Repetitive change like week or seasonality of year
  -h(t) = Elements that is irregular effect like Holiday
  
- In sample test
 ![image](https://user-images.githubusercontent.com/100894816/172273744-6d807f15-9131-49e3-8090-db28967cca2a.png)



- Out of Sample test
  - prophet result
  - bdi
  - market price
  - economic element
  - US dollar
- Prameter change

- Rate of change 
 - We want to use the rate of change & prediction rate of change 
 - ![image](https://user-images.githubusercontent.com/100894816/173766578-ea93a6b2-b344-413b-b1bc-ddc99d6d0d5e.png)
 
 - ![image](https://user-images.githubusercontent.com/100894816/173766706-e724967a-cc4f-4c1a-9e25-f509633c18b0.png)
  - iron / WTI rate of change

 - Result is bad.

- File
- prophet_pred_all.csv  
-경로 : dataset → prophet_pred → prophet_pred_all.csv  
-기간 : 2019년 1월 1일 ~ 2019년 3월 31일 (**3개월 예측**)
-prophet 단변량 /features 예측값 (30개 전체)
- prophet_pred_all_year.csv  
-경로 : dataset → prophet_pred → prophet_pred_all_year.csv  
-기간 : 2019년 1월 1일 ~ 2019년 12월 31일 (**12개월 예측**)
-prophet 단변량 /features 예측값 (30개 전체)
- project_dataset_pred.csv  
-경로 : dataset → prophet_pred → project_dataset_pred.csv  
-기간 : 2019년 1월 1일 ~ 2019년 3월 31일 (**3개월 예측**)
-prophet 단변량 /features 예측값 (9개)
- project_dataset.csv  
-경로 : dataset → project_dataset.csv  
-기간 : 2011년 1월 1일 ~ 2019년 12월 31일 (**실제 데이터**)

-------

- Code  (code파일→prophet+Xgboost)
- Xgboost_blackcoal_all
-변수 30개 
-기간 3개월
-파라미터 Maxdepth 10 / 20/ 30
- Xgboost_blackcoal_v1
-변수 9개 (상관관계 분석을 통해 도출)
-기간 3개월
-파라미터 Maxdepth 10 / 20/ 30
- Xgboost_blackcoal_v2
-변수 4개 (3개월 그래프가 잘나온것)
-기간 3개월
-파라미터 Maxdepth 10 / 20/ 30
- Xgboost_blackcoal_all_year
-변수 30개 
-기간 1년
-파라미터 Maxdepth 10 / 20/ 30
- Prophet_maker_all
-feature prediction by prophet
- Prophet_maker
- feature prediction by prophet (graph)
- Xgboost_recursive_all
 -변수 30개 / 31개 (t-1시점 blackcoal)
 -val기간 1년(마지막값에 y_pred로 검증), 
 -예측기간: 1일 기준 업데이트 되는 방식
- Prophet_ rate of change
 -Rate of change each feature -> prophet prediction
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

 
 
 

4) Xgboost
- many-to-many
- with prophet prediction we test the xgboost Model, it works well.
- so, we make 


- With Xgboost only, we make the Model. Feature is made by recursive xgboost.
- ![image](https://user-images.githubusercontent.com/100894816/173767237-851bc3b5-1534-4d7c-8826-83270a441cc5.png)
- ![image](https://user-images.githubusercontent.com/100894816/173767296-42f590eb-d80a-454c-8fde-07201f3063dd.png)
- Result is so various depending on each features. 

- ![image](https://user-images.githubusercontent.com/100894816/173767839-c0c2c283-0442-46a2-be8f-329f120b1e40.png)
 - recursive model
- ![image](https://user-images.githubusercontent.com/100894816/173767963-57c6dcf6-cd45-4cd4-8ee1-d804d5bcaa54.png)
 - recursive medel + time t-1 Coal_price 
- ![image](https://user-images.githubusercontent.com/100894816/173768126-8320d078-37e3-49b1-b168-fd34c16e001c.png)
 - prophet + xgboost with daily data 30


3) lstm
many-to-many 
  
5) 1D convolution
many-to-many
