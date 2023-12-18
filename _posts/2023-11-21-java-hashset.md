---
title: "[Java] HashSet의 개념"
excerpt: "자바의 비선형 자료구조 중 하나인 HashSet에 대해 알아보자"

categories:
    - Java
tags:
    - [Java, Set, HashSet, Data Structure]

toc: true
toc_sticky: true

date: 2023-11-21
last_modified_at: 2023-11-21
---

## **HashSet이란?**
HashSet은 set 인터페이스를 구현한 클래스이다. 비선형적인 구조로 값의 순서가 저장되지 않아 인덱스가 없다. 중복값을 허용하지 않는 것이 특징이며 null을 허용하지만 하나의 null값만 저장할 수 있다.   
HashSet에는 인덱스가 없어서 값을 추가하거나 삭제할 때 먼저 Set 내부에 그 값이 있는지 검색해야 한다. 이런 이유로 List보다 속도가 느리다.   
HashSet은 값을 저장하기 전에 객체의 hashcode() 메소드를 호출한다. 여기서 hashcode는 객체의 주소값을 변환하여 생성한 고유한 정수값이다. hashcode가 일치하면 HashSet은 equals() 메소드로 두 객체를 비교하고 결과로 true가 반환되면 최종적으로 두 객체가 같다고 판단한다.

## **HashSet 사용**
### **HashSet 선언 및 값 추가**
**코드**
```java
import java.util.HashSet;

public class Main {
    public static void main(String[] args){
        HashSet<Integer> set = new HashSet<>();
        set.add(1);
        set.add(2);
        set.add(3);

        System.out.println(set.size());
    }
}
```

**결과**
> 3

HashSet을 사용하려면 java.util.HashSet을 임포트해줘야 한다. 값을 추가할 때는 add() 메소드로 추가할 수 있고 size() 메소드를 사용하면 HashSet의 크기를 얻을 수 있다.

### **HashSet 값 삭제**
```java
HashSet<Integer> set = new HashSet<>(Arrays.asList(1, 2, 3));
set.remove(3);
set.clear();
```

HashSet에서 값을 제거할 때는 remove() 메소드를 사용한다. remove() 메소드에 매개변수로 전달된 값이 HashSet 내부에 존재한다면 값을 삭제하고 true를 반환하고, 내부에 값이 없다면 false를 반환한다. clear() 메소드를 사용하면 HashSet 내부의 모든 값을 삭제할 수 있다.

### **HashSet 값 출력**
```java
import java.util.Arrays;
import java.util.HashSet;
import java.util.Iterator;

public class Main {
    public static void main(String[] args){
        HashSet<Integer> set = new HashSet<>(Arrays.asList(1, 2, 3));
        System.out.println(set);

        Iterator iter = set.iterator();
        while(iter.hasNext()){
            System.out.println(iter.next());
        }
    }
}
```

**결과**
> [1, 2, 3]   
1   
2   
3

HashSet을 그냥 출력하면 전체 값이 []로 묶여서 반환된다. HashSet에 저장된 값을 하나씩 출력하고 싶다면 Iterator를 사용해야 한다. Iterator는 반복자로서 자료구조 내부를 순회하면서 값을 반환하는 객체이다. Set에는 인덱스가 없기 때문에 Iterator로 값에 접근해서 하나씩 출력해야 한다.   
Iterator를 사용할 때는 hasNext() 메소드로 다음 값이 있는지 확인하고 next() 메소드로 값을 가져온다.

### **HashSet 값 검색**
```java
HashSet<Integer> set = new HashSet<>(Arrays.asList(1, 2, 3));
System.out.println(set.contains(1));    //true
```

HashSet 내부에 어떤 값이 존재하는지 확인하려면 contains() 메소드를 사용하면 된다. 매개변수로 전달된 값이 존재한다면 true, 존재하지 않는다면 false를 반환한다.

## **참고**
<https://coding-factory.tistory.com/554>