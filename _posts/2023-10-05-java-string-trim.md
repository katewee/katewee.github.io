---
title: "[Java] 문자열 공백 제거"
excerpt: "Java에서 문자열의 공백을 제거하는 방법 정리"

categories:
    - Java
tags:
    - [Java, String, Trim, Strip, ReplaceAll]

toc: true
toc_sticky: true

date: 2023-10-05
last_modified_at: 2023-10-05
---

문자열 앞뒤 공백, 내부 공백을 제거하는 방법에 대해 정리하고자 한다.

## **trim()**
trim()은 문자열의 앞뒤 공백을 제거해주는 함수이다. 기존 문자열을 변화시키지 않고 새로운 문자열을 반환하므로 반환값을 받기 위한 변수를 선언해서 할당해야 한다.

**코드**
```java
public class Main {
    public static void main(String[] args){
        String str = " Hello new world ";
        String nstr = str.trim();
        System.out.println("'" + nstr + "'");
    }
}
```

**결과**
> 'Hello new world'

앞뒤의 공백만 제거된 것을 확인할 수 있다.

## **strip()**
strip()은 java 11 이상부터 지원하는 공백 제거 함수이다.

**코드**
```java
public class Main {
    public static void main(String[] args){
        String str = "   Hello new world ";
        String nstr = str.strip();
        System.out.println("원본 문자열: '" + str + "'");
        System.out.println("공백 제거 문자열: '" + nstr + "'");
    }
}
```

**결과**
> 원본 문자열: '   Hello new world '
공백 제거 문자열: 'Hello new world'

## **trim()과 strip() 차이**
trim()은 '\u0020' 이하의 공백들만 제거하는 반면 strip() 은 유니코드의 모든 공백을 제거한다.
strip()을 사용하면 더 많은 종류의 공백을 제거할 수 있다.

## **replaceAll()**
replaceAll("A", "B") 함수는 A를 B로 대체하는 함수이다. 이 함수를 활용하면 문자열 내부의 공백을 제거할 수 있다.

**코드**
```java
public class Main {
    public static void main(String[] args){
        String str = "   Hello New World ";
        String nstr = str.replaceAll(" ", "");
        
        System.out.println("원본 문자열: '" + str + "'");
        System.out.println("공백 제거 문자열: '" + nstr + "'");
    }
}
```

**결과**
> 원본 문자열: '   Hello New World '
공백 제거 문자열: 'HelloNewWorld'

앞뒤 공백과 단어 사이의 공백이 모두 제거된 것을 확인할 수 있다.
