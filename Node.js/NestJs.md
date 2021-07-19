## NestJS

### Introduce

- Nest는 테스트 가능성이 높고 확장 가능하며 느슨하게 결합되고 유지 관리가 쉬운 애플리케이션을 손쉽게 만들 수 있는 애플리케이션 아키텍처를 즉시 제공하는 것을 목표로한다.
- 이 아키텍처는 Angular에서 크게 영감을 받았다.
- TypeScript (순수 JavaScript와의 호환성 유지 )로 빌드되고 OOP (Object Oriented Programming), FP (Functional Programming) 및 FRP (Functional Reactive Programming) 요소가 결합되었다.
- 기업에 큰 중점에 둔다. (자유도 높은 express에 비해 고정된 틀이 잡혀있어 팀원이 많아져도 협업 및 유지보수가 쉽다)

### Architecture

- 기본적으로 express를 내장하고 있다.
- 최상위 main.ts는 필수다. 이름 변경 불가능
- module, controller, service 형태로 구성되어있으며 app.module은 최상위 모듈
- module을 큰 기능 단위로 생각하면 된다. DDD 디자인 패턴 개념과 비슷한듯 하다.
- controller는 express의 router 느낌
- 클래스에 함수 기능을 추가 할 수 있는 데코레이터를 사용한다.

---

### 느낀점

express로 개발할 때 https://github.com/santiq/bulletproof-nodejs 등 여러 아키텍처를 참고하며 좋은 아키텍처에 대해 고민을 많이 했었다. 따라서 NestJs에서 나오는 서비스 로직, 비즈니스 로직 분리 및 아키텍처 구성은 크게 어렵지 않게 느껴졌다.
OOP적인 개발이 익숙하지는 않아 이것만 익숙해지면 개발하는데 큰 이슈는 없어 보인다.

> Reference : https://nomadcoders.co/nestjs-fundamentals
