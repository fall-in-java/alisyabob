# 새로운 날짜와 시간 API
- java.time 패키지는 LocalDate, LocalTime, LocalDateTime, Instant, Duration, Period 등 다양한 클래스를 제공한다.

## LocalDate와 LocalTime 사용
- LocalDate 인스턴스는 시간을 제외한 날짜를 표현하는 불변객체
- 연도, 달, 요일 등을 반환하는 메서드를 제공한다.

```java
    LocalDate date = LocalDate.of(2022, 4, 23);   //2022-04-22
    int year = date.getYear();  //2022
    Month month = date.getMonth();  //APRIL
    int day = date.getDayOfMonth();  //23
    DayOfWeek dow = date.getDayOfWeek();  //SATURDAY
    int len = date.lengthOfMonth();  // 30 (4월의 일 수)
    boolean leap = date.isLeapYear();  // false(윤년아님)
    LocalDate today = LocalDate.now();  // 현재 날짜 정보
```


