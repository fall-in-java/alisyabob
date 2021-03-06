# Stream
## 스트림
### 스트림이란 무엇인가
- 자바 8 API에 새로 추가된 기능
- 스트림을 사용하면 선언형으로 데이터를 처리할 수 있다.
- 데이터 컬렉션 반복을 멋있게 처리하는 기능

#### 장점
- 선언형 : 간결하고 가독성 좋음
- 조립가능 : 유연성이 좋아진다
- 병렬화 : 성능이 좋아짐

1. java7버전코드
```java
List<Dish> lowCaloricDishes = new ArrayList<>();
for(Dish dish: menu){
    if(dish.getCalories()<400){
        lowCaloricDishes.add(dish);
    }
}

Collections.sort(lowCaloricDishes, new Comparator<Dish>(){
    public int compare(Dish dish1, Dish dish2){
        return Integer.compare(dish1.getCalories(), dish2.getCalories());
    }
});

List<String> lowCaloricDishesName = new ArrayList<>();
for(Dish dish: lowCaloricDishes){
    lowCaloricDishesName.add(dish.getName());
}
```
- lowCaloricDishes 가비지 변수로 temp같이 컨테이너 역할을 하는 중간변수 느낌
- for문 돌리면서 가비지변수에 값을 넣고 그 값을 다시 정렬하고 다시 이름만 가져와서 넣어준다.

2. java8버전
```java
List<String> lowCaloricDishesName = menu.stream().
filter(dish -> dish.getCalories() < 400)
.sorted(comparing(Dish::getCalories))
.map(Dish::getName)
.limit(3)
.collect(toList());
```

#### ParallelStream()
- ParallelStream()은 멀티코어 아키텍처에서 병렬로 실행한다고 한다.
- 병렬처리해서 순서를 보장하지 않는다.
- default로 어플리케이션이 구동되는 스펙에 따라 스레드 수가 결정됨
- 음 뭔소린지 모르겠군 써보고 테스트 해보면서 더 파봐야 겠다.

### 스트림 시작하기
- 데이터 처리 연산을 지원하도록 소스에서 추출된 연속된 요소
- 파이프라이닝 : 스트림 연산은 스트림 연산끼리 연결해서 커다란 파이프라인 구성 할수 있도록 스트림 반환
- 내부반복 : 명시적으로 반복하는 컬렌션과 다르게 스트림은 내부반복 지원

### 외부반복과 내부반복
- 외부반복 : 사용자가 컬렉션 인터페이스를 사용하려면 직접 요소를 반복해야한다.
- 내부반복 : 반면 내부반복은 스트림 라이브러리를 알아서 처리하고 결과 스트림값을 어딘가에 저장한다.
- ex)내부반복
```
오늘 공부 다했니? <br>
아니요 javascript 공부 안했어요
```

```
오늘 공부 다했니?<br>
아니요 Component 공부 안했어요
```

```
오늘 공부 다했니?<br>
아니요 State 공부 안했어요
```

```
오늘 공부 다했니?<br>
아니요 Redux 공부 안했어요
```
  - 컬렉션을 항목을 하나씩 가져와서 처리한다.
- ex) 외부반복
```
오늘 공부 다했니?<br>
아니요 js, Component, State, Redux 공부 안했어요
```
- 병렬처리를 할 수 있다.
- 최적화를 달성할 수 있다.


### 스트림 연산
```java
List<String> lowCaloricDishesName = menu.stream().
filter(dish -> dish.getCalories() < 400)
.map(Dish::getName)
.limit(3)
.collect(toList());
```
- filter, map, limit는 서로 연결되어 파이프라인을 형성한다.
- filter, map, limit : 중간연산
- collect(toList()) : 스트림을 리스트로 반환