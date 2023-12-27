#### random() 메소드
- 0.0 ~ 1.0 미만의 임의 double형 값을 하나 생성
```java
System.out.println((int)(Math.random() * 100));
System.out.println((int)(Math.random() * 6));   

// >> 0 ~ 99
// >> 0 ~ 5
```

#### abs() 메소드
- 전달된 값의 절대값을 반환 
```java
System.out.println(Math.abs(-10));   
System.out.println(Math.abs(210));  

// >> 10
// >> 210
```

#### ceil(), floor(), round() 메소드
- ceil() : 전달된 값의 소수점 첫번째 자리로 올림 후 double형으로 반환
- floor() : 전달된 값의 소수점 첫번째 자리로 내림 후 double형으로 반환 
- round() : 전달된 값의 소수점 첫번째 자리로 반올림 후 int형으로 반환
``` java
System.out.println(Math.ceil(10.0));      
System.out.println(Math.ceil(10.3));      

// >> 10.0
// >> 11.0

System.out.println(Math.floor(10.3));
System.out.println(Math.floor(10.9));

// >> 10.0
// >> 10.0

System.out.println(Math.round(10.4)); 
System.out.println(Math.round(10.5));

// >> 10
// >> 11
```

#### max(), min() 메소드
- max() : 전달된 두 값을 비교해서 큰 값을 반환
- min() : 전달된 두 값을 비교해서 작은 값을 반환
```java
System.out.println(Math.max(3.14, 3.14159)); 
System.out.println(Math.min(3.14, 3.14159)); 

// >> 3.14159
// >> 3.14
```

#### pow(), sqrt() 메소드
- pow(a, b) : a의 b승을 double 형으로 반환
- sqrt() :  전달된 값의 제곱근을 double 형으로 반환
```java
System.out.println(Math.pow(5, 2));
System.out.println(Math.sqrt(25));  

// >> 25.0
// >> 5.0
```