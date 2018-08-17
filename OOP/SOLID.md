# 객체 지향 설계 5원칙
- [스프링 입문을 위한 자바 객체 지향의 원리와 이해](https://book.naver.com/bookdb/book_detail.nhn?bid=8920762)를 읽고 정리.

## 객체 지향 설계 5원칙 - SOLID
- 객체 지향의 특성을 올바르게 사용하는 방법, 즉 객체 지향 언어를 이용해 객체 지향 프로그램을 올바르게 설계해 나가는 방법이나 원칙이 존재할까?
- 객체 지향 설계(OOD; Object Oriented Design)의 정수라고 할 수 있는 5원칙이 집대성됐는데, 바로 SOLID다.
    - SRP(Single Responsibility Principle) :단일 책임 원칙
    - OCP(Open Closed Principle) : 개방 폐쇄 원칙
    - LSP(Liskov Subsitution Principle) : 리스코프 치환 원칙
    - ISP(Interface Segregation Principle) : 인터페이스 분리 원칙
    - DIP(Dependency Inversion Principle) : 의존 역전 원칙
- 하늘에서 뚝 떨어진 원칙이라기 보다는 응집도는 높이고 (High Cohension), 결합도는 낮추라(Loose Coupling)는 고전 원칙을 객체 지향의 관점에서 재정립한 것이라고 할 수 있다.
```
결합도와 응집도
- 결합도는 모듈(클래스) 간의 상호 의존 정도로서 결합도가 낮으면 모듈 간의 상호 의존성이 줄어들어 객체의 재사용이나 수정, 유지보수가 용이하다
- 응집도는 하나의 모듈 내부에 존재하는 구성 요소들의 기능적 관련성으로, 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져 재사용이나 기능의 수정, 유지보수가 용이하다.
<http://toby.epril.com/?p=727> 참고
```
- SOLID는 객체 지향 프로그램을 구성하는 속성, 메서드, 클래스, 객체, 패키지, 모듈, 라이브러리, 프레임워크, 아키텍처 등 다양한 곳에 다양하게 적용
- SOLID가 개념이긴 하지만 우리가 만드는 제품, 즉 소프트웨어에 녹여 내야 하는 개념이다.
- SOLID는 객체 지향 4대 특성을 발판으로 하고 디자인 패턴의 뼈대이며 스프링 프레임워크의 근간이기도 하다.

### SRP - 단일 책임 원칙
- `어떤 클래스를 변경해야 하는 이유는 오직 하나뿐이어야 한다  - 로버트 C.마틴`
- 클래스를 예로 들면 하나의 클래스는 각각 하나의 역할과 책임만 갖게 해야한다.(클래스를 역할과 책임에 따라 분리해서)
- 메서드가 단일 책임 원칙을 지키지 않을 경우 나타나는 대표적인 냄새가 바로 분기 처리를 위한 if문 이다.
- 단일 책임 원칙과 가장 관계가 깊은 것은 바로 모델링 과정을 담당하는 `추상화`
    - 애플리케이션의 경계를 정하고 추상화를 통해 클래스들을 선별하고 속성과 메서드를 설계할 때 반드시 단일 책임 원칙을 고려하는 습관을 들이자.
    - 또한 리팩토링을 통해 코드를 개선할 때도 단일 책임 원칙을 적용할 곳이 있는지 꼼곰히 살피자.

### OCP - 개방 폐쇄 원칙
- `소프트웨어 엔티티(클래스, 모듈, 함수 등)는 확장에 대해서는 열려 있어야 하지만 변경에 대해서는 닫혀 있어야 한다. - 로버트 C.마틴`
    - 의역 : `자신의 확장에는 열려 있고, 주변의 변화에 대해서는 닫혀 있어야 한다.`
- 예. JDBC
    - JDBC를 사용하는 클라이언트는 데이터베이스가 오라클에서 MySQL로 바뀌더라도 Connection을 설정하는 부분 외에는 따로 설정할 필요가 없다. Connection 설정 부분을 별도의 설정 파일로 분리해두면 클라이언트 코드는 단 한줄도 변경할 필요가 없다.
    - 오라클을 MySQL이나 MS-SQL로 교체할 때 자바 애플리케이션은 JDBC 인터페이스라고 하는 완충 장치로 인해 변화에 영향을 받지 않는다.
    - 바로 `자바 애플리케이션은 데이터베이스라고 하는 주변의 변화에 닫혀 있는 것`이다.
    - 데이터베이스를 교체한다는 것은 `데이터베이스가 자신의 확장에는 열려 있다는 것`이다.
- 개방 폐쇄 원칙을 무시하고 프로그램을 작성하면 객체 지향 프로그래밍의 가장 큰 장점인 유연성, 재사용성, 유지보수성 등을 얻을 수 없다.
- 따라서 반드시 지켜야 할 원칙.
- 스프링 프레임워크 - 개방 폐쇄 원칙을 교과서적으로 활용하고 있음을 확인 가능.

### LSP - 리스코프 치환 원칙
- `서브 타입은 언제나 자신의 기반 타입(base type)으로 교체할 수 있어야 한다 - 로버트 C.마틴`
- 상속에 대해 설명하면서 객체 지향에서의 상속은 조직도나 계층도가 아닌 분류도가 돼야 한다고 했다.
    - 하위 클래스 is kind of 상위 클래스 - 하위 분류는 상위 분류의 한 종류다.
- 위의 문장대로 구현된 프로그램이라면 이미 리스코프 치환 원칙을 잘 지키고 있다고 할 수 있다.
- 하지만 위 문장대로 구현되지 않은 코드가 존재할 수 있는데 바로 상속이 조직도나 계층도 형태로 구축된 경우다.
- 아버지를 상위 클래스 (기반 타입)로 하는 딸이라는 하위 클래스 (서브 타입)가 있다.
    - 아버지 춘향이 = new 딸() - 리스코프 치환 원칙 위배
    - 이상하다! 딸에게 아빠의 역할을 맡기고 있다. 아버지 객체가 가진 행위(메서드)를 할 수 있어야하는데 춘향이에게 어떤 역할을 시킬 수 있을까?
- 동물 뽀로로 = new 펭귄() - 분류도 형태, 논리적인 흠이 없다. 리스코프 치환원칙 만족
- `하위 클래스 인스턴스는 상위형 객체 참조 변수에 대입해 상위 클래스의 인스턴스 역할을 하는데 문제가 없어야 한다.`
- 결국 리스코프 치환 원칙은 객체 지향의 상속이라는 특성을 올바르게 활용하면 자연스럽게 얻게 되는 것이다.

### ISP - 인터페이스 분리 원칙
- `클라이언트는 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안 된다 - 로버트 C.마틴`
- 결론적으로 단일 책임 원칙(SRP)과 인터페이스 분할 원칙(ISP)은 같은 문제에 대한 두 가지 다른 해결책이라고 볼 수 있다.
- 프로젝트 요구사항과 설계자의 취향에 따라 단일 책임 원칙이나 인터페이스 분할 원칙 중 하나를 선택해서 설계할 수 있다.
- 하지만 특별한 경우가 아니라면 단일 책임 원칙을 적용하는 것이 더 좋은 해결책이라고 할 수 있다.
- 인터페이스 분할 원칙을 이야기할 때 항상 함께 등장하는 원칙 중 하나로 인터페이스 최소주의 원칙이라는 것이 있다. 인터페이스를 통해 메서드를 외부에 제공할 때는 최소한의 메서드만 제공하라는 것.

### DIP - 의존 역전 원칙
- `고차원 모듈은 저차원 모듈에 의존하면 안 된다. 이 두 모듈 모두 다른 추상화된 것에 의존해야 한다.`
- `추상화된 것은 구체적인 것에 의존하면 안 된다. 구체적인 것이 추상화된 것에 의존해야 한다`
- `자주 변경되는 구체(COncrete) 클래스에 의존하지 마라 - 로버트 C.마틴`
- 자신보다 변하기 쉬운 것에 의존하던 것을 추상화된 인터페이스나 상위 클래스를 두어 변하기 쉬운 것의 변화에 영향받지 않게 하는 것이 의존 역적 원칙.
- 의존 역전 원칙을 의역하면
    - `자신보다 변하기 쉬운 것에 의존하지 마라.`
- 상위 클래일수록, 인터페이스일수록, 추상 클래스일수록 변하지 않을 가능성이 높기에 하위 클래스나 구체 클래스가 아닌 상위 클래스, 인터페이스, 추상 클래스를 통해 의존하라는 것이 바로 의존 역전 원칙이다.
- 의존 역전 원칙을 적용한 대표적인 사례는 이전에 OCP에서 설명했던 JDBC에서 확인할 수 있다.

### 정리 - 객체 지향 세계와 SOLID
- SOLID는 객체 지향을 올바르게 프로그램에 녹여내기 위한 원칙이다.
- SOLID를 이야기할 때 빼놓을 수 없는 것이 SoC이다.
- SoC (Separation of Concerns) 관심사의 분리.
    - 관심이 같은 것끼리는 하나의 객체 안으로 또는 친한 객체로 모으고, 관심이 다른 것은 가능한 한 따로 떨어져 서로 영향을 주지 않도록 분리하라는 것이다.
    - 하나의 속성, 하나의 메서드, 하나의 클래스, 하나의 모듈, 또는 하나의 패키지에는 하나의 관심사만 들어 있어야 한다는 것
    - SoC를 적용하면 자연스럽게 SRP, ISP, OCP에 도달하게 된다.
- SOLID 원칙을 적용하면 소스 파일의 개수는 더 많아지는 경향이 있다. 하지만 이렇게 많아진 파일이 논리를 더욱 잘 분할하고, 잘 표현하기에 이해하기 쉽고, 개발하기 쉬우며, 유지와 관리, 보수하기 쉬운 소스가 만들어진다.
- 스프링 프레임 워크를 이해하기 위해서는 객체지향의 특성과 설계 원칙, 그리고 디자인 패턴에 대해 이해하여야 한다.