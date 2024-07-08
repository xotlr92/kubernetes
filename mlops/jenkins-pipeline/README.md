# Jenkins Pipeline

## agent

---
### aws-cli
- ECR 정보를 가져오기 위한 conatiner
### kaniko
- 이미지 Build를 위한 container

## stages

---
### Check for Changes in Target Folder
- github의 특정 경로(docker/mlops)에서 push가 발생하면 이후 stage를 실행할 수 있도록 설정
- env TARGET_FOLDERS에 해당하는 경로에 event 발생 시 수행
### Checkout
- github checkout
### Run Git
- 빌드될 프로젝트의 이름을 가져오도록 설정
### Check App Version
- 이미지에 사용될 애플리케이션의 버전 정보를 가져옴
### Update TAG Version
- ECR TAG 리스트를 가져오고 최신 버전으로 push 될 수 있도록 버전 설정 알고리즘 적용
### Build & Pushㅈ
- kaniko 빌드 수행