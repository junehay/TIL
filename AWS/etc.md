## EC2 instance

ap-northeast-2(Seoul) 기준

- t2.micro - 2a, 2c AZ 지원
- t3.micro - 2a,2b,2c,2d AZ 지원

### 문제해결

ECS 구성 중 ECS 인스턴스가 자동 생성이 되지 않음.
- 에러 - 'Reason: No Container Instances were found in your cluster.'

**이유**

ECS 인스턴스로 t2.micro를 선택하고, ECS 인스턴스가 위치한 Subnet의 AZ는 ap-northeast-2d 사용.

❗️❗️ **t2.micro만 프리티어 지원이 되는줄 알았는데, t1, t3모두 지원 가능하다. 앞으로 성능 좋고 모든 AZ 지원 가능한 t3 사용하자.**
