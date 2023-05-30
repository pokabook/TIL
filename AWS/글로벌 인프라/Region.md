# Region

### Region

![region.png](https://t1.daumcdn.net/cfile/tistory/99747A335C5900B834)


- AWS의 서비스가 제공되는 리소스의 지리적 위치
- 각 리전 각 글로벌 네트워크 백본(Back born) 연결
- 재해복구(DR) 설계 : 2개 이상의 리전에 시스템을 배치
- 각 리전에는 고유의 코드가 부여됨
- 지역(ap)-지리적위치(northeast)-순번(2)

| 코드             | 이름              | 가용영역 |
|----------------|-----------------|------|
| us-east-2      | US East (Ohio)  | 3    |
| us-east-1      | 미국 동부(버지니아 북부)  | 6    |
| us-west-1      | 미국 서부(캘리포니아 북부) | 3    |
| us-west-2      | 미국 서부(오리건)      | 4    |
| af-south-1     | 아프리카(케이프타운)     | 3    |
| ap-east-1      | 아시아 태평양(홍콩)     | 3    |
| ap-south-2     | 아시아 태평양(하이데라바드) | 3    |
| ap-southeast-3 | 아시아 태평양(자카르타)   | 3    |
| ap-southeast-4 | 아시아 태평양(멜버른)    | 3    |
| ap-south-1     | 아시아 태평양(뭄바이)    | 3    |
| ap-northeast-3 | 아시아 태평양(오사카)    | 3    |
| ap-northeast-2 | 아시아 태평양(서울)     | 4    |
| ap-southeast-1 | 아시아 태평양(싱가포르)   | 3    |
| ap-southeast-2 | 아시아 태평양(시드니)    | 3    |
| ap-northeast-1 | 아시아 태평양(도쿄)     | 4    |
| ca-central-1   | 캐나다(중부)         | 3    |
| eu-central-1   | 유럽(프랑크푸르트)      | 3    |
| eu-west-1      | 유럽(아일랜드)        | 3    |
| eu-west-2      | 유럽(런던)          | 3    |
| eu-south-1     | 유럽(밀라노)         | 3    |
| eu-west-3      | 유럽(파리)          | 3    |
| eu-south-2     | 유럽(스페인)         | 3    |
| eu-north-1     | 유럽(스톡홀름)        | 3    |
| eu-central-2   | 유럽(취리히)         | 3    |
| me-south-1     | 중동(바레인)         | 3    |
| me-central-1   | 중동(UAE)         | 3    |
| sa-east-1      | 남아메리카(상파울루)     | 3    |

### 리전 선택 고려사항 - 1

---

- [리전 별 서비스 제공 유무 확인](https://aws.amazon.com/ko/about-aws/global-infrastructure/regional-product-services/)

### 리전 선택 고려사항 - 2

---

- [리전 별 서비스 가격 확인](https://calculator.aws/#/addService)