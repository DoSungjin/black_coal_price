# 🕋B**lackcoal_price**

# ❓**Why is forecasting important?**

- There has always been a demand for price prediction. From a company's point of view, inventory management of raw materials is the key to cost control. In this way, from the raw material market, which is the basis of business, the production volume that determines the production of goods, that is, the demand itself, is also required. If you derive insight into the market while modeling, and go through the process of developing the model through the derived information, prediction can give a lot of information to business management, not just prediction.
   
# https://mnc.ai/?p=11

# 📅Period
- 2022-05-23 ~ 2022-07-20

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
 
# EDA
-![image](https://user-images.githubusercontent.com/100894816/174795217-06686582-9984-44d4-a4f7-37d72a2b76e3.png)
- ![image](https://user-images.githubusercontent.com/100894816/174795239-26ad8397-61fb-4c39-ba2a-bc95bd44942f.png)
- ![image](https://user-images.githubusercontent.com/100894816/174795264-a07d818e-4b73-41ba-925a-6b7b243c3c25.png)
- ![image](https://user-images.githubusercontent.com/100894816/174795305-2dcccf90-4416-4e36-8200-cea0b2dc9ab7.png)
- ![image](https://user-images.githubusercontent.com/100894816/174795326-7e82b1d0-56bc-474b-adb1-2aa992a851bf.png)
-![image](https://user-images.githubusercontent.com/100894816/174795339-ed0bbfbb-2329-4f52-8d17-d4aed98bc1a3.png)
-![image](https://user-images.githubusercontent.com/100894816/174795354-65209a99-f8a3-4760-932d-6d39a78225ef.png)
-![image](https://user-images.githubusercontent.com/100894816/174795369-84ddbc97-5f0f-4ff7-80a6-b1c99a81d7ad.png)
- In time series prediction, correlation is not important. However, we used it as a reference.
- ![image](https://user-images.githubusercontent.com/100894816/174796891-9fd5f554-c77c-4b92-9e87-fde638bd3536.png)
- https://www.notion.so/1-f7d955c5de3f4820a94fe7192ce39e94
- https://www.notion.so/Corrcoef-1-0c4fe9aff61f47aa8828f2a195914ab0
- https://www.notion.so/covarian-correlation-p-value-1-1bc3a7f4338e4e9cbe36cfe65f9152fd
- https://www.notion.so/linear-regresstion-1-ef985825e6f94fa991c9a9e2f9ad4065
- https://www.notion.so/Graph-with-Coal-62ae8d33fbac466d88df2e5a8b6bfda7

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
  - y(t) = g(t) + s(t) + h(t) +et
  - g(t) = Trend that has not repetitive elements
  - s(t) = Repetitive change like week or seasonality of year
  - h(t) = Elements that is irregular effect like Holiday
  
- In sample test
 ![image](https://user-images.githubusercontent.com/100894816/172273744-6d807f15-9131-49e3-8090-db28967cca2a.png)



- Out of Sample test
  - prophet result
  - ![image](https://user-images.githubusercontent.com/100894816/174795466-f00a457d-ce87-456e-a0df-7c4d5780a1bd.png)
  - ![image](https://user-images.githubusercontent.com/100894816/174795491-df7f8bb6-cbb3-4161-b797-1ce49086795b.png)
  - ![image](https://user-images.githubusercontent.com/100894816/174795545-1a550e54-8d02-49cc-8613-d53686318dd1.png)
- iron
- ![image](https://user-images.githubusercontent.com/100894816/174795578-4c872b28-5000-4789-a4eb-9affce16a85d.png)
- Brent_fut
- ![image](https://user-images.githubusercontent.com/100894816/174795919-33b8003c-7bb7-4d30-af4d-563a085de2c8.png)
- copper_fut
- ![image](https://user-images.githubusercontent.com/100894816/174796022-b1238900-0e02-41b6-bad4-056d08082564.png)
- WTI_fut
- ![image](https://user-images.githubusercontent.com/100894816/174796066-4693e6b9-eb1d-434e-8e77-dfec6a26832d.png)
- bdi
- ![image](https://user-images.githubusercontent.com/100894816/174796109-125bcf7a-bfd9-4524-af00-34a2d07621e2.png)
- USD/AUD
- ![image](https://user-images.githubusercontent.com/100894816/174796141-617aacd0-7d13-4d7b-bfc2-b2555e7bd0a4.png)
- USD/CAD
- ![image](https://user-images.githubusercontent.com/100894816/174796167-d6482f92-a7f9-4318-ba08-3a9c4802387c.png)
- USD/COP
- ![image](https://user-images.githubusercontent.com/100894816/174796225-21c9d465-ba70-4da7-b770-586d24678f22.png)
- USD/ZAR
- ![image](https://user-images.githubusercontent.com/100894816/174796274-cdb057a2-cec7-4cda-85a1-46f08e7a042c.png)
- 상하이종합지수
- ![image](https://user-images.githubusercontent.com/100894816/174796306-27a2dec8-aa9b-4edb-8329-602aff5a699a.png)
- 인도지수(India)
- ![image](https://user-images.githubusercontent.com/100894816/174796366-a1482c62-62df-4b14-b7c7-4972a58f15dd.png)

- Prameter change

- Rate of change 
 - We want to use the rate of change & prediction rate of change 
 - ![image](https://user-images.githubusercontent.com/100894816/173766578-ea93a6b2-b344-413b-b1bc-ddc99d6d0d5e.png)
 
 - ![image](https://user-images.githubusercontent.com/100894816/173766706-e724967a-cc4f-4c1a-9e25-f509633c18b0.png)
  - iron / WTI rate of change

 - Result is bad.

- File
- prophet_pred_all.csv  
-경로 : dataset → prophet_pred → prophet_pred_all.csv -> (prophet_pred_final.csv - changed)   
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

---------------------------------------------------------------------------------

- Code  (code파일→prophet+Xgboost)


- Xgboost_blackcoal_all
- 변수 30개 
- 기간 3개월
- 파라미터 Maxdepth 10 / 20/ 30


- Xgboost_blackcoal_v1
- 변수 9개 (상관관계 분석을 통해 도출)
- 기간 3개월
- 파라미터 Maxdepth 10 / 20/ 30


- Xgboost_blackcoal_v2
-변수 4개 (3개월 그래프가 잘나온것)
-기간 3개월
-파라미터 Maxdepth 10 / 20/ 30


- Xgboost_blackcoal_all_year
-변수 30개 
-기간 1년
-파라미터 Maxdepth 10 / 20/ 30


- Prophet_maker_all
- feature prediction by prophet
- Prophet_maker
- feature prediction by prophet (graph)


- Xgboost_recursive_all
 -변수 30개 / 31개 (t-1시점 blackcoal)
 -val기간 1년(마지막값에 y_pred로 검증), 
 -예측기간: 1일 기준 업데이트 되는 방식
 
 
- Prophet_ rate of change

- Rate of change each feature -> prophet prediction
 
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

 
 
 

4) Prophet + Xgboost
- many-to-many
- with prophet prediction we test the xgboost Model, it works well.
- In sample test first
- ![image](https://user-images.githubusercontent.com/100894816/174830101-eda1b937-402a-4181-b6cb-ca4e652f4758.png)

- so, we make 
- recursive(val 1year)
- ![image](https://user-images.githubusercontent.com/100894816/174829377-d3e0aebc-905f-4a3c-be4f-34f5f55e12f1.png)
- recursive(val 3month)
- ![image](https://user-images.githubusercontent.com/100894816/174829590-4060ad19-854a-4952-91e5-98be88fb6449.png)
- recursive(val 3month/t-1 prediction->add feature)
- ![image](https://user-images.githubusercontent.com/100894816/174829630-6c39b493-3716-4c73-a38b-7892f13f1f05.png)
- recursive(val 1day)
- ![image](https://user-images.githubusercontent.com/100894816/174829946-8727755f-c36b-4914-978f-c04dad0b35a5.png)
- recursive(train=val)
- ![image](https://user-images.githubusercontent.com/100894816/174830522-aa43fc0e-a3ea-41ac-84ee-05a582ba7735.png)


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
- 
5) XGBoost(AR+recursive)
- X feature make
- iron
- ![image](https://user-images.githubusercontent.com/100894816/174831126-7b5560e2-09d1-4bf1-99a1-4d7d8d033c12.png)
- brent_fut
- ![image](https://user-images.githubusercontent.com/100894816/174831195-61a2677e-d10f-42e0-9ecd-916d20a61845.png)
- WTI_fut
- ![image](https://user-images.githubusercontent.com/100894816/174831247-e0491da1-3b26-4658-8e5c-7103daaf4caf.png)
- LNG_fut
- ![image](https://user-images.githubusercontent.com/100894816/174831307-fdec7f78-b673-4a09-8662-0c4acb507400.png)
- AUD_dollar
- ![image](https://user-images.githubusercontent.com/100894816/174831375-20821c39-e9b4-418e-8561-d6015fa4b633.png)
- CAD_dollar
- ![image](https://user-images.githubusercontent.com/100894816/174831417-cee708d6-852c-48b1-82b9-11273b034f45.png)
- ZAR_dollar
- ![image](https://user-images.githubusercontent.com/100894816/174831511-6e7fb618-7cdf-439f-98ec-6ab416c5cc02.png)
- DXY
- ![image](https://user-images.githubusercontent.com/100894816/174831555-72f39cba-cd39-41f3-bafb-0cec93b2da24.png)
- SHA
- ![image](https://user-images.githubusercontent.com/100894816/174832094-1142784d-3122-4300-bda5-b9c3a7c69eab.png)
- BSE
- ![image](https://user-images.githubusercontent.com/100894816/174832159-cfe97cc3-622e-4160-9f12-9d7042a45ef3.png)
- DJI
- ![image](https://user-images.githubusercontent.com/100894816/174831617-ff64f181-9d07-4a08-8ffd-4f1d92546db1.png)
- IXIC
- ![image](https://user-images.githubusercontent.com/100894816/174831684-b68a76bd-7dfb-4932-848e-fbce3cc78fbe.png)

6) lstm
many-to-many 
  
7) 1D convolution
many-to-many
