# MLOps

## CI/CD 자동화

---

### CI Pipeline
Update Dockerfile --> Push Github --> Github Webhook Trigger --> Jenkins --> Build Image --> Push ECR

### Upgrade Release
- Before
  - 이미지 버전 관리를 위해 TAG를 수동으로 설정해야합니다.
  - 각 빌드마다 Jenkinsfile을 중복해서 설정해야합니다.
  - 인스턴스에 설정된 IAM이 아닌 .aws/credentails 파일을 참조하도록 설정되어있습니다.

- After
  - 이미지 버전 관리를 자동으로 수행합니다.
  - 공통된 Jenkinsfile을 사용하여 유저는 Dockerfile만 작성하면됩니다.
  - 인스턴스에 설정된 IAM을 사용하여 AWS와 통신합니다.

### Jenkins Pipeline 작성
- jenkins-pipeline/Jenkinsfile 참조