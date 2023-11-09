# IAM (Identity and Access Management)

### IAM (Identity and Access Management)

- AWS 리소스에 대한 액세스를 안전하게 제어할 수 있는 서비스
- IAM User / User Group / Role / Policy로 구성
- 리전에 속하는 서비스가 아닌 글로벌 서비스

### Policy

![Policy](https://github.com/pokabook/TIL/assets/103029701/18399005-1b64-4985-b056-7520b3850271)

- 리소스의 접근 권한을 정의하는 정책
- `JSON` 문서 형식으로 이루어짐
- 정책이 명시되지 않은 경우 기본적으로 모든 요청이 거부됨
- User, User Group, IAM Role 에 할당 가능

### IAM 정책 JSON 문서 구조


```json
{
  "Statement" : [{
    "Effect" : "effect",
    "Action" : "action",
    "Resource" : "arn",
    "Condition" : {
      "condition" : {
        "key" : "value"
      }
    }
  }]
}
```

- **Effect**
    - Statement에 대한 `Access` 또는 `Deny`
- **Action**
    - 권한에 대한 작업 목록
- **Resource**
    - 권한이 적용되는 리소스
- **Condition**
    - 정책이 적용되는 세부 조건 (옵션 사항)

### Policy Type

- **RBAC (Role Base Access Control)**
 
  - 역할기반 접근제어 정책
  - 역할을 생성하고 해당 역할이 접근할 수 있는 리소스를 명시한 후 접근을 제어

    ![RBAC](https://github.com/pokabook/TIL/assets/103029701/0f737c51-0734-4b2f-bf01-9b783b44daac)
- **ABAC (Attribute Base Access Control)**
  - 속성기반 접근제어 정책
  - 역할을 tag로 정의하고 연결하여 사용
  - 빠르고 확장성 있는 접근 제어가 가능

    ![ABAC](https://github.com/pokabook/TIL/assets/103029701/841ac112-b3aa-45f9-8558-06ba3f7d3d1b)

### Role

![Role](https://github.com/pokabook/TIL/assets/103029701/866de4f7-f7cf-464b-ae07-08048770a796)

- AWS 리소스에서 사용하는 자격증명
- 특정 AWS 서비스가 다른 AWS 서비스에 엑세스 하여 작업을 수행할 때 필요한 권한
- 정책을 연결하여 IAM 역할에 작업 수행에 필요한 권한을 부여

### IAM 보안 도구 (IAM Security Tools)

- **IAM 자격 증명 보고서 (Credentials Report)**
  
  - 계정의 모든 사용자와 암호, 엑세스 키, MFA 디바이스 등의 자격 증명 상태에 대한 보고서를 다운로드

- **IAM 엑세스 관리자 (Access Advisor)**

  - 사용자 또는 역할이 허용된 서비스에 마지막으로 엑세스하려고 시도한 시간을 표시
  - 이 정보를 사용해 필요 이상으로 부여된 권한을 재정의 하는데 참고 가능

### IAM Policy Simulator

- [AWS 계정의 IAM 사용자, 그룹, 역할에 연결된 정책을 테스트](https://policysim.aws.amazon.com)
