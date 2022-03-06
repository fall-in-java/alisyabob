# null 대신 Optional 클래스
- 개발을 한번이라도 해봣다면 NullPointerException을 봣을 것이다.
 
### null 때문에 발생하는 문제
- 에러의 근원
- 코드를 어지럽힌다 : null 체크로 인해 가독성이 떨어짐
- 아무 의미가 없다
- 자바 철학에 위배된다 : 자바개발자는 모든 포인터를 숨겼다. 하지만 예외가 하나 있는데 그게 바로 null
- 형식 시스템에 구멍을 만든다 : null은 무형식이라 정보가 없는데 이걸 쓰기 시작하면 null이 정말 많아졌을 때 뭐가뭔지 구분이 안간다.

## Optional 클래스
- java8의 등장과 함께 생긴 클래스로 선택형 값을 캡슐화 하는 클래스이다.
- ex)  어떤사람이 차를 소유하고 있지 않다. -> Person 클래스의 car 변수는 null이 된다.
  - 하지만 null을 할당하는게 아니라 변수형 Optional<Car>로 설정 할 수 있다.
  
- ![image](https://user-images.githubusercontent.com/48196352/156928232-2278f339-8b87-4e12-aab3-f0bf78030e62.png)
- 값이 있을 경우 Optional 클래스는 값을 감싼다.
- 값이 없으면 Optional.empty 메서드로 Optional을 반환
- 값이 없을 수 있다는 것을 명시적으로 보여줄 수 있음 

## Optional 적용 패턴
#### 빈 Optional
```java
Optional<Car> optCar = Optional.empty();
```
- 빈 Optional 객체를 얻을 수 있다.

#### null이 아닌 값으로 Optional 만들기
```java
Optional<Car> optCar = Optional.of(car);
```
- car이 null이라면 즉시 NullPointerException이 발생

#### null값으로 Optional 만들기
```java
Optional<Car> optCar = Optional.ofNullable(car);
```
- null값을 저장할 수 있는 Optional을 만들 수 있다.
- car가 null이면 빈 Optional 객체가 반환된다.

