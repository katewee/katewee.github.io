---
title: "[Java] 문자열의 format 함수"
excerpt: "문자열의 형식을 지정하는 format 함수에 대한 정리"

categories:
    - Java
tags:
    - [Java, String, Format]

toc: true
toc_sticky: true

date: 2023-11-12
last_modified_at: 2023-11-12
---

코딩테스트 문제를 풀면서 문자열의 뒤에 문자를 추가하는 것은 많이 해봤는데 문자열의 앞에 새로운 문자를 추가하려고 하니까 방법이 잘 생각나지 않았다. 그래서 이번에는 문자열의 앞에 문자열을 추가할 때 활용할 수 있는 format 함수에 대해 알아보려고 한다.

## **String.format()**
format 함수는 두 가지 인자를 입력받는다. 첫 번째 인자는 출력할 문자열의 서식을 나타내고 두 번째 인자는 서식에서 사용자가 지정한 위치에 들어갈 값이다. String.format()을 사용한 예는 다음과 같다.

```java
public static void main(String[] args){
    int num = 7;
    String str = String.format("num의 값은 %d입니다.", num);
    System.out.println(str);
}
```

**결과**
> num의 값은 7입니다.

결과를 보면 서식에서 %d로 표현한 자리에 num의 값이 대입되어 출력된 것을 확인할 수 있다. format 함수는 c언어에서 사용하는 printf 함수와 비슷하다. 서식 부분을 바꿔주면 정수 외에도 다양한 자료형을 대입할 수 있다.

## **자료형에 따른 format 함수 활용**
다양한 자료형에 맞는 서식은 다음과 같다.   

| 자료형    | 서식    |   
|:----------|:-------|   
| boolean   | %b     |   
| String    | %s     |   
| character | %c     |   
| int       | %d     |   
| float     | %f     |   
| character | %c     |

## **수 및 문자열 가공**
### **수 앞에 0 채우기**
서식을 쓸 때 "%0nd"로 작성하면 문자열의 앞을 0으로 채운 결과를 반환한다. 이때 0은 n번 반복되는 것이 아니라, n에서 출력하려는 숫자의 자릿수를 뺀 만큼 반복된다.

```java
String str = String.format("%05d", 123);
System.out.println(str);
```

**결과**
> 00123

### **문자열 앞에 공백 채우기**
수와 비슷하게 "%ns" 형식으로 작성하면 문자열의 앞을 공백으로 채운 문자열이 반환된다. 문자열의 앞이 아닌 뒤에 추가하고 싶다면 "%-ns" 형식으로 작성하면된다.

```java
String str = String.format("%4s", "abc");
System.out.println("'" + str + "'");
```

**결과**
> ' abc'

format 함수와 replaceAll 함수를 함께 사용하면 문자열의 앞에 원하는 문자열을 추가할 수 있다.

### **세 자리마다 콤마(,) 넣기**
금액을 표현할 때 활용하기 좋은 방법이다. "%,d" 형식으로 작성하면 세 자리마다 ,가 입력된 결과를 반환한다.

```java
String str = String.format("%,d", 123456789);
System.out.println(str);
```

**결과**
> 123,456,789

### **8진수, 16진수로 출력**
8진수는 "%o", 16진수는 "%x"를 사용하여 출력할 수 있다.

```java
String str1 = String.format("%o", 10);
String str2 = String.format("%x", 10);
System.out.println("10을 8진수로 변환하면 " + str1);
System.out.println("10을 16진수로 변환하면 " + str2);
```

**결과**
> 10을 8진수로 변환하면 12   
10을 16진수로 변환하면 a

## **참고**
<https://engineer-mole.tistory.com/403>   
<https://www.devkuma.com/docs/java/string-format/>