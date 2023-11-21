---
title: "[Java] 리스트를 배열로 변환하기"
excerpt: "Java에서 리스트를 배열로 변환하는 방법을 알아보자"

categories:
    - Java
tags:
    - [Java, List, Array, 자료구조]

toc: true
toc_sticky: true

date: 2023-09-09
last_modified_at: 2023-09-09
---

## **개요**
지난번에는 배열을 리스트로 변환하는 방법에 대해서 알아봤다. 이번 글에서는 리스트를 배열로 바꾸는 방법에 대해서 정리하려고 한다.

## **반복문 사용**
리스트를 배열로 변환하는 작업도 반복문을 사용해서 할 수 있다.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args){
        List<Integer> list = new ArrayList<>();
        list.add(1);
        list.add(2);
        list.add(3);

        int[] arr = new int[list.size()];
        for(int i = 0; i < list.size(); i++){
            arr[i] = list.get(i);
        }

        System.out.println(Arrays.toString(arr));
    }
}
```
리스트의 사이즈와 같은 길이의 배열을 생성하고 차례대로 리스트의 원소를 넣어주면 된다.

## **toArray 메서드 사용**
List 인터페이스에는 toArray라는 메서드가 있다. 이 메서드를 이용하면 리스트를 배열로 변환할 수 있다.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args){
        List<String> list = new ArrayList<>();
        list.add("a");
        list.add("b");
        list.add("c");

        String[] arr1 = list.toArray(new String[0]);
        String[] arr2 = new String[list.size()];
        arr2 = list.toArray(arr2);

        System.out.println(Arrays.toString(arr1));
        System.out.println(Arrays.toString(arr2));
    }
}
```
arr1은 배열을 선언함과 동시에 리스트를 배열로 변환해서 할당하는 방법이다. arr2는 우선 리스트와 같은 길이의 배열을 만든 후에 리스트로부터 변환한 배열을 할당하는 방법이다.

## **Stream 사용**
Java 8 이상부터는 Stream을 사용할 수 있는데 이것을 이용해서 리스트를 배열로 변환할 수 있다.

```java
String[] arr = list.stream().toArray(String[]::new);
```

### **기본형 배열로 변환하기**
리스트는 Reference Type만 지원하므로 Primitive Type의 배열로 변환하려면 다른 방법을 사용해야 한다. 방법은 두 가지가 있는데 하나는 반복문을 사용하는 것이고 다른 하나는 Stream을 사용하는 것이다.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args){
        List<Integer> list = new ArrayList<>();
        list.add(1);
        list.add(2);
        list.add(3);

        int[] arr = list.stream().mapToInt(i->i).toArray();

        System.out.println(Arrays.toString(arr));
    }
}
```
반복문을 이용한 코드는 위에서 작성했으므로 생략한다.

## **마무리**
이번 글에서는 리스트를 배열로 변환하는 방법을 정리해봤다. 리스트와 배열은 코딩테스트 문제에도 자주 나오고 평소에도 자주 사용하는 자료구조인 만큼 개념을 제대로 정리하는 게 중요하다고 느꼈다.   
개인적으로 자바의 배열은 c언어와는 다르게 배열을 선언할 때 크기값을 상수로 하지 않아도 된다는 점이 편리했다. 여러 언어를 공부하면서 이런 차이를 알아가는 것도 소소한 재미인 것 같다. 