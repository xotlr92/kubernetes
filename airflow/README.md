# Airflow

## KEDA 설정

---

### Worker

#### KEDA Option
* worker-kedaautoscaler MySQL Type 추가
  * Airflow Helm Chart에서는 MySQL을 사용한 KEDA Worker Autoscaling을 지원하지 않기 때문에 해당 옵션을 추가
  * queryValue는 1로 설정하여 concurrency(16)가 임계값을 넘어가면 동작하도록 설정
  * templates/workers/worker-kedaautoscaler.yaml 파일 참조
* Secret 추가
  * MySQL Keda 구성(https://keda.sh/docs/2.10/scalers/mysql/)을 참조하여 Secret, TriggerAuthentication를 구성
  * Secret에서 mysql_conn_str를 구성할 때에는 base64 Encoding을 반드시 수행
* Value 수정
  * ::Decimal 구문 오류 제거
  * metadataConnection.protocol에 mysql 추가

### TargetGroupBinding

#### Template
* targetGroupBinding을 생성하기 위한 템플릿 작성
* templates/targetgroupbinding.yaml 참조

#### Value
* dev, prod 구분을 위한 targetGroupBinding 옵션을 base Helm Chart values에 추가
* dev/phase/{env}.yaml에서 targetGroupARN을 변경하여 targetGroupBinding을 환경에 맞게 생성