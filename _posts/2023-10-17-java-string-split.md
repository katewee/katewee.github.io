---
title: "[Java] 문자열 자르기"
excerpt: "Java에서 문자열을 사용자가 지정한 방법으로 자르는 방법"

categories:
    - Java
tags:
    - [Java, String, Split, Substring]

toc: true
toc_sticky: true

date: 2023-10-17
last_modified_at: 2023-10-17
---

요즘 문자열을 가공하는 방법을 공부하고 있다. 이번에는 ",", "-" 등의 기호를 기준으로 문자열을 분할하는 방법을 정리해보려고 한다.

## **split(String regex)**
split() 함수는 정규표현식이나 문자를 기준으로 문자열을 자르고 배열에 담아 반환한다.

```java
public class Main {
    public static void main(String[] args){
        String str = "Apple,Banana,Orange";
        String[] arr = str.split(",");

        System.out.println(arr[0]);
        System.out.println(arr[1]);
        System.out.println(arr[2]);
    }
}
```
위의 코드에서는 str을 ","를 기준으로 잘라서 arr에 저장했다.

**결과**
> Apple
Banana
Orange

arr의 원소를 확인해보면 ","를 기준으로 분할된 문자열이 담겨있다.

## **split(String regex, int limit)**
split() 함수에 두 번째 인자로 정수를 전달하면 정수값을 크기로 갖는 배열을 반환한다.

**코드**
```java
public class Main {
    public static void main(String[] args){
        String str = "Apple,Banana,Orange,Melon,Plum,Kiwi";
        String[] arr = str.split(",", 3);

        for(int i = 0; i < arr.length; i++){
            System.out.println(arr[i]);
        }
    }
}
```

**결과**
> Apple
Banana
Orange,Melon,Plum,Kiwi

배열의 크기를 3으로 지정한 결과이다. 첫 번째, 두 번째 자리에 차례대로 분할된 문자열이 저장되고 세 번째 자리에 나머지 문자열이 저장된 것을 알 수 있다.

## **substring()**
substring() 함수는 인자로 전달받은 인덱스를 기준으로 문자열을 자르고 반환한다. 원본 문자열을 변경하지 않고 새로운 문자열을 반환하므로 변수를 선언하여 저장해야 한다.

### **substring(int begin)**
substring()에 인자를 하나만 전달하면 해당 인덱스부터 문자열의 끝까지 잘라서 반환한다.

**코드**
```java
public class Main {
    public static void main(String[] args){
        String str = "Banana";
        String subStr = str.substring(2);

        System.out.println(subStr);
    }
}
```

**결과**
> nana

### **substring(int begin, int end)**
인자를 두 개 전달할 경우 인덱스를 기준으로 begin부터 end - 1까지 자른 문자열을 반환한다.

**코드**
```java
public class Main {
    public static void main(String[] args){
        String str = "Banana";
        String subStr = str.substring(2, 5);

        System.out.println(subStr);
    }
}
```

**결과**
> nan

함수 실행 결과로 2번 인덱스부터 4번 인덱스까지 문자열이 잘려서 반환되었다.

