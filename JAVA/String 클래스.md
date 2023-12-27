- 문자열 자료형
	- 리터럴 방식 
		- `String a = "java";
	- 객체 사용 방식
		- `String b = new String("Java");
	- 객체 사용 방식과 리터럴 방식의 ==메모리 저장 차이==
		- 객체 사용 방식은 ==힙 메모리==에 데이터 저장
		- 리터럴 방식의 경우 ==문자열 상수풀==이라는 특별한 공간에 저장
			- ==리터럴 방식 : 최적화에 도움==
- 참조 자료형이고, Wrapper 클래스 
- 주요 메서드
	- length
		- 문자열의 길이를 int형으로 반환한다.
	- equals
		- ex) `a.equals(b)
			- a와 b가 같은지 비교한다.
		- boolean(true, false) 반환
		- equalsIgnoreCase : 대소문자 구분x
	- indexOf
		- 문자열에서 특정 문자가 처음 등장하는 위치의 인덱스 값을 반환한다.
		- lastIndexOf  : 마지막으로 나타나는 위치의 인덱스 값을 반환한다.
	- contains
		- 문자열에서 특정 문자열이 포함되어 있는지를 boolean형으로 반환한다.
	- charAt
		- 문자열에서 특정 위치(index)의 문자(char)를 반환한다.
	- replace
		- 문자열 중 특정 문자열을 다른 문자열로 모두 바꾸고자 할 때 사용한다.
		- 원본은 바뀌지 않고 새로운 문자열을 반환한다.
	- substring(a, b)
		- 문자열에서 a부터 b 미만까지의 index에 해당하는 문자열을 뽑아낼 경우 사용
		- `st1.substring(0,5)`
			- 0~4번째 문자열을 반환
			- 마찬가지로 원본은 바뀌지 않는다.
	- toUpperCase / toLowerCase
		- 문자열을 대문자, 소문자로 변환
	- Trim
		- 좌우에 있는 모든 공백을 제거한다.
		- java 11 이후로는 ==.strip() 사용==
	- split
		- 문자열을 특정 구분자로 분리하여 String배열로 반환한다.
	- join()
		- 여러 문자열을 하나로 결합, 각 문자열 사이에는 지정한 구분자가 삽입된다.
		- 클래스 메서드임으로 String.join() 사용
- StringBuffer
	- 문자열을 추가하거나 변경할 때 주로 사용하는 객체
	- 주요 메서드
		- append
			- 문자열 마지막에 문자열을 추가할 수 있다.
		- insert
			- 특정 인덱스에 위치에 원하는 문자열을 삽입
		- reverse
			- 문자열을 뒤집는데 사용된다.
```java
String my_string = "love";
StringBuffer sb = new StringBuffer(my_string);
// stringbuffer 선언
String answer = sb.reverse().toString();
// reverse() 함수 사용
System.out.println(answer);


// >> evol
```
- 
	- 그외 메서드는 String과 동일
- StringBuilder
	- StringBuffer와 같은 기능을 하는 객체지만 성능이 더 뛰어나다.
- StringBuffer와 StringBuilder의 차이점

| 특징       | StringBuffer     | StringBuilder                   |
| ---------- |:---------------- |:------------------------------- |
| 동기화 여부 | 지원함           | 지원하지 않음                    |
| 성능       | 느리다           | 빠르다                          |
| 사용 용도   | 멀티 스레드 환경 | 단일 스레드 환경 또는 성능 우선 |

- 동기화 (synchronization)
	- 동기화란 멀티 스레드 환경에서 데이터의 일관성을 보장하기 위한 것.
	- 만약 멀티 스레드 환경에서 A스레드 B스레드가 한 객체를 동시에 작업할 때, A가 값을 바꾸면 B는 A가 변경한 값이 아닌 이전 값으로 작업을 하는 것이다. 이때 데이터의 일관성이 깨진다. 
		- StringBuffer는 synchronized 속성을 가지고 있어 A스레드가 작업하는 동안 B스레드는 접근할 수 없다.
		- StringBuilder는 지원하지 않기에 여러 스레드가 동시에 접근해 예측할 수 없는 결과가 발생할 수 있다.
- 성능
	- 따라서 동기화를 지원하는 StringBuffer는 성능이 저하돼서 느리고 동기화를 지원하지 않는 StringBuilder는 빠르다.
- 사용 용도
	- 멀티 스레드 환경에서는 데이터의 일관성을 지키기 위해 StringBuffer를 사용한다.
	- 단일 스레드, 성능을 우선시하는 환경에서는 StringBuilder를 사용한다.



