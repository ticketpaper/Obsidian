### 메인 함수

```
public class Main // <접근 제어자> class <클래스명>
{
	public static void main(String[] args) { // 프로그램의 시작점
		System.out.println("Hello World");
	}
}
```

public static void main(String\[\] args) {  
                 . . .  
}

main 함수로 프로그램의 시작점입니다.

반드시 이대로 main 함수를 만들어야 하고 안 그러고 실행 시 오류가 발생합니다.

### System.out.println();

표준 출력으로 한 줄을 출력하는 함수입니다.

자바의 출력은 아래와 같습니다.

```
System.out.println("Hello! World!");
```

장점으로는 자동 줄 넘김이 된다는 것과 "+" 이용해 문자와 숫자를 더해 문자열로 만들 수 있다는 점입니다.

단점으로는 출력 형식을 지정해 주지 못한다는 점입니다. 이를 해결하는 방법으로는 printf()를 사용하는 것입니다.

### System.out.printf();

```
System.out.printf("Hello world!\n");
```

#### printf()의 지시자

| 지시자 | 설명 |
| --- | --- |
| %b | 불리언(boolean) 형식으로 출력 |
| %d | 10진(decimal) 정수의 형식으로 출력 |
| %o | 8진(octal) 정수의 형식으로 출력 |
| %x, %X | 16진(hexa-decimal) 정수의 형식으로 출력 |
| %f | 부동 소수점(floating-point)의 형식으로 출력 |
| %e, %E | 지수(exponent) 표현식의 형식으로 출력 |
| %c | 문자(character)로 출력 |
| %s | 문자열(string)로 출력 |