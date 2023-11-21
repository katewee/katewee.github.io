---
title: "[Java] 배열을 리스트로 변환하기"
excerpt: "Java에서 배열을 리스트로 변환하는 방법을 알아보자"

categories:
    - Java
tags:
    - [Java, List, Array, 자료구조]

toc: true
toc_sticky: true

date: 2023-09-08
last_modified_at: 2023-09-08
---

## **개요**
코딩테스트 기초 문제를 풀다보면 배열을 리스트로 변환해야 하는 경우가 있다.   
앞으로 자주 사용할 문법이니까 이번에 확실하게 정리하려고 한다.

## **반복문 사용**
우선 간단하게 반복문을 사용하는 방법이 있다.

**코드**
```java
public static void main(String[] args){
    int[] arr = {1, 2, 3};
    List<Integer> list = new ArrayList<>();

    for(int n : arr){
        list.add(n);
    }

    System.out.println(list);
}
```
배열의 길이만큼 반복문을 돌려서 원소를 한 개씩 리스트에 넣어준다. 

**결과**
> [1, 2, 3]

## **asList 메서드 사용**
두 번째 방법은 Arrays 클래스의 asList 메서드를 사용하는 방법이다. asList 메서드를 사용하려면 java.util.Arrays 패키지를 임포트해야 한다.

**코드**
```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args){
        Integer[] arr = {1, 2, 3};
        List<Integer> list = Arrays.asList(arr);

        System.out.println(list);
    }
}
```

**결과**
> [1, 2, 3]

위의 방법으로 변환한 리스트에는 값을 추가하거나 삭제할 수 없다. 만약 추가하려고 하면 UnsupportedOperationException이 발생한다. asList 메서드의 결과로 반환되는 리스트는 우리가 평소에 사용하는 ArrayList가 아니라서 이런 예외가 생긴다. 이 리스트를 ArrayList로 바꾸려면 ArrayList의 생성자로 감싸주어야 한다.

**코드**
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args){
        Integer[] arr = {1, 2, 3};
        List<Integer> list = new ArrayList<>(Arrays.asList(arr));
        list.add(4);

        System.out.println(list);
    }
}
```

**결과**
> [1, 2, 3, 4]

## **Stream 사용**
리스트는 Primitive type을 지원하지 않으므로 int형 배열 등은 boxed 메서드를 이용해서 Wrapper type으로 바꿔줘야 한다. 이 과정에서 Java 8 이상부터 지원되는 Stream을 사용한다.

**코드**
```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args){
        int[] arr = {1, 2, 3};
        List<Integer> list = Arrays.stream(arr).boxed().collect(Collectors.toList());

        System.out.println(list);
    }
}
```

**결과**
> [1, 2, 3]

## **마무리**
이번 글에서는 배열을 리스트로 변환하는 방법을 정리해보았다. 매번 문제를 풀 때마다 검색해서 해결했는데 직접 글을 작성하면서 정리하니까 이 내용이 머리에 오래 남을 것 같다. 다음에는 리스트를 배열로 변환하는 방법도 정리하겠다. 