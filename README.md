# cfn-automation-amazon-forecast
Automate the deployment of an Amazon Forecast time-series forecasting model
## 설치
- 번호 순서대로 stack 생성
- 생성한 s3 버킷에 스택 이름으로 폴더를 만들고 'dada/forecast'에 파일 압축을 풀어서 업로드
```
"Path.$": "States.Format('{}{}{}','s3://',$.GetParameters.DatasetS3Bucket,'/{stack-name-02}/tts/')",
```
- Step Functions 콘솔에서 `Create-Dataset-Group` 실행
- Step Functions 콘솔에서 `Import-Dataset` 실행
- Step Functions 콘솔에서 `Create-Predictor` 실행
- Parameter Store 콘솔 이동
  - `/forecast/<StackName>/Forecast/PredictorArn` 값을 위에서 생성된 예측기의 ARN 입력
  - `/forecast/<StackName>/Forecast/Generate`의 `FALSE` -> `TRUE` 로 변경
- Step Functions 콘솔에서 `Create-Forecast` 실행

## Reference
- https://aws.amazon.com/ko/blogs/machine-learning/automate-the-deployment-of-an-amazon-forecast-time-series-forecasting-model/
