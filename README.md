# US_President_Election_2024
# 2024 미국 대선 데이터분석

- __주제__ : 미국 대선 관련 뉴스 기사 & 트위터 & 토론 텍스트를 활용하여 감성 분석 및 대선 예측
- __결과보고서__ : [Here](https://github.com/b00kkk/US_President_Election_2024/blob/main/results_report.pdf
  )
- __프로젝트 수행기간__ : 2024.09.30 ~ 2024.10.31(10월 초에 코드 완성 후 크롤링 기간 대기)

# 결과보고서
## 분석 개요
- 2021년 기사에 따르면 검색량을 보면 어느 후보자가 당선이 될지 예측할 수 있다고 함
- 2024년 미국 대선은 투표 전날까지도 지지율이 비슷한 지역이 다수
- 이러한 이유로 2024년 미국 대통령 선거에 대해 후보자 언급 빈도수를 확인해 보고, 추가적으로 후보자 관련 트윗 감성분석도 실시


## 데이터 수집
- [대선 토론](https://www.kaggle.com/datasets/sohambhagwat/presidential-debate-2-transcript2024)
- news: [reason](https://reason.com/category/politics/elections/election-2024/), [CBS](https://www.cbsnews.com/feature/election-2024/), [npr](https://www.npr.org/sections/elections/)
- X(twitter)

## 데이터 전처리
- 수집된 데이터를 토큰화
- 토크화 된 데이터를 품사 태그 후 어간 추출
- 역토큰화 실행

## 데이터 시각화
### `대선토론`
![image](https://github.com/user-attachments/assets/f8f69696-498e-440e-a78e-995873e0bcf0)
> 해리스는 트럼프 언급 빈도가 높은 것을 확인할 수 있음
### `뉴스`
![image](https://github.com/user-attachments/assets/b0d07fad-7e87-40aa-9cbe-e08088de6e59)
> 기사 개수와 언론사에 관계없이 트럼프의 언급수가 해리스보다 높음
![image](https://github.com/user-attachments/assets/24ef4573-55bb-462c-b410-09f637c85b5a)
> 기간별로 봤을 때도 항상 트럼프의 언급수가 높음
### `X(Twitter)`
![image](https://github.com/user-attachments/assets/4fba5ede-e915-4377-a079-40add034e596)
#### 트럼프
> 암살 미수 지역인 펜실베니아가 많이 나옴
> 
> comrade, together과 같은 가치를 많이 사용함
> 
> maga는 'make america great again'이라는 슬로건임
#### 해리스
> Hurricane helene 의 언급이 많은 것을 보아 피해 지역에 관한 내용을 많이 작성한 것을 확인
>
> 이전 후보자인 biden에 관한 빈도가 높음
>
> freedom, violent 와 같은 단어가 많이 사용됨

![image](https://github.com/user-attachments/assets/07a01d53-aab0-46eb-8fa9-6129a9599f0d)
> VADER 감성 분석 사용
>
> 짧은 문장인 소셜미디어에 용이함
>
> 감성 점수를 극대화하기 위해 compound 값에 따라 임계값으로 감성 점수를 설정함

## 모델링
### ARIMA

|![image](https://github.com/user-attachments/assets/1b34ab13-a187-4349-9b9f-9f1c3b74e887)|![image](https://github.com/user-attachments/assets/5ab85b58-b935-48d9-9a29-f989318327ff)|
|---------------------------------------------------|--------------------------------------------------------|


> 시계열 데이터를 이용해 선거 당일 11월 5일 감성점수를 예측하기 위해 ARIMA 사용
> - LSTM 대비 RMSE, MAE 값이 낮게 나와 ARIMA 모형으로 선정
> 트럼프 : 0.083
>
> 해리스 : -0.227

## 결론
- 언론에서의 언급수를 비교했을 때 해리스의 언급수 보다 트럼프의 언급수가 더 많음
- 감성점수를 확인해보니 선거당일 트럼프의 감성점수가 더 높음
