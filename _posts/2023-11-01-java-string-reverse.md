---
title: "[Java] 문자열 뒤집기"
excerpt: "Java에서 문자열을 뒤집는 방법 정리"

categories:
    - Java
tags:
    - [Java, String, StringBuilder, StringBuffer]

toc: true
toc_sticky: true

date: 2023-11-01
last_modified_at: 2023-11-01
---

문자열 가공 방법 중의 하나인 문자열 뒤집기에 대해 다뤄보려고 한다.

## **반복문**
우선 간단하게 반복문을 사용한 방법이 있다.   
문자열의 끝에서부터 반복문을 돌리면서 새로운 변수에 문자열을 구성하고 있는 문자를 하나씩 할당하는 방법이다.

**코드**
```java
public class Main {
    public static void main(String[] args){
        String str = "Hello";
        String reverse = "";

        for(int i = str.length() - 1; i >= 0; i--){
            reverse += str.charAt(i);
        }

        System.out.println(reverse);
    }
}
```

**결과**
> olleH

## **StringBuilder/StringBuffer의 reverse()**
StringBuilder와 StringBuffer 클래스는 자체적으로 문자열을 뒤집어서 반환하는 reverse() 메서드를 지원한다.

**코드**
```java
public class Main {
    public static void main(String[] args){
        String str = "Hello";
        StringBuilder sb = new StringBuilder(str).reverse();
        StringBuffer sbf = new StringBuffer(str).reverse();

        System.out.println("StringBuilder: " + sb.toString());
        System.out.println("StringBuffer: " + sbf.toString());
    }
}
```

**결과**
> StringBuilder: olleH
StringBuffer: olleH

두 클래스 모두 같은 결과를 반환한다.