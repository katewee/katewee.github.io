---
title: "[Java] 배열을 정렬하는 법"
excerpt: "Java에서 배열을 정렬하는 다양한 방법을 정리"

categories:
    - Java
tags:
    - [Java, Array, Sort, Collections]

toc: true
toc_sticky: true

date: 2023-09-20
last_modified_at: 2023-09-20
---

이번 글에서는 배열을 정렬하는 다양한 방법을 정리하려고 한다.

## **Arrays.sort()**
### **오름차순 정렬**
Arrays.sort()는 int, String 상관 없이 사용할 수 있고 오름차순으로 배열을 정렬한다. String의 경우 아스키코드 값을 기준으로 정렬한다. Arrays.sort()는 기존 배열의 순서를 바꿔주므로 새로운 배열에 결과값을 할당할 필요가 없다.

**코드**
```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args){
        int[] arr = {10, 2, 35, 89, 17};
        Arrays.sort(arr);

        System.out.println(Arrays.toString(arr));
    }
}
```

**결과**
> [2, 10, 17, 35, 89]

### **내림차순 정렬**
내림차순으로 배열을 정렬하고 싶다면 sort()의 인자에 Collections.reversOrder()를 전달해야 한다.
Collections.reverseOrder()는 Comparator 객체이다. Comparator는 직접 구현할 수도 있다.

**코드**
```java
import java.util.Arrays;
import java.util.Collections;

public class Main {
    public static void main(String[] args){
        Integer[] arr = {10, 2, 35, 89, 17};
        Arrays.sort(arr, Collections.reverseOrder());

        System.out.println(Arrays.toString(arr));
    }
}
```
Collections.reverseOrder()를 사용하여 정수형 배열을 정렬할 때 주의할 점은 int가 아닌 Integer를 사용해야 한다는 점이다.

**결과**
> [89, 35, 17, 10, 2]

## **Comparator 구현**
문자열을 아스키코드 값이 아닌 길이를 기준으로 정렬하는 경우 Comparator를 직접 구현해야 한다.

**코드**
```java
import java.util.Arrays;
import java.util.Comparator;

public class Main {
    public static void main(String[] args){
        String[] arr = {"Apple", "Kiwi", "Orange", "Banana", "Watermelon", "Cherry"};
        Arrays.sort(arr, new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return o1.length() - o2.length();
            }
        });

        System.out.println(Arrays.toString(arr));
    }
}
```
내림차순으로 정렬하고 싶다면 return 부분의 순서를 바꿔주면 된다.

**결과**
> [Kiwi, Apple, Orange, Banana, Cherry, Watermelon]

## **객체 배열 정렬**
사용자가 정의한 객체의 배열을 정렬하려면 해당 객체에 Comparable을 구현해야 한다. Comparable이란 객체의 기본 정렬 방법을 정의하는 것이다.
참고로 위에서 나왔던 Comparator는 기본 정렬 방법 외에 추가로 정렬 방법을 정의할 때 사용한다.

**Custom 객체 정의 코드**
```java
public static class Fruit implements Comparable<Fruit> {
        private String name;
        private int price;
        public Fruit(String name, int price) {
            this.name = name;
            this.price = price;
        }

        @Override
        public String toString() {
            return "{name: " + name + ", price: " + price + "}";
        }

        @Override
        public int compareTo(@NotNull Fruit fruit) {
            return this.price - fruit.price;
        }
    }
```
우선 name, price 필드를 갖는 Fruit 클래스를 정의했다. 여기서 compareTo() 메서드는 자기 자신과 인자로 전달되는 객체의 price를 비교한다.

**Fruit 정렬 코드**
```java
public static void main(String[] args){
        Fruit[] arr = {
                new Fruit("Apple", 100),
                new Fruit("Kiwi", 500),
                new Fruit("Orange", 200),
                new Fruit("Banana", 50),
                new Fruit("Watermelon", 880),
                new Fruit("Cherry", 10)
        };

        Arrays.sort(arr);

        System.out.println(Arrays.toString(arr));
    }
```

**결과**
> [{name: Cherry, price: 10}, {name: Banana, price: 50}, {name: Apple, price: 100}, {name: Orange, price: 200}, {name: Kiwi, price: 500}, {name: Watermelon, price: 880}]

결과를 보면 Fruit의 가격을 기준으로 오름차순 정렬된 것을 확인할 수 있다.

## **참고**
<https://codechacha.com/ko/java-sorting-array/>
