---
title: "Chirpy 테마에서 사용할 마크다운 문법 정리"
excerpt: "마크다운 문법을 사용하여 블로그에 포스팅해보자"

categories:
    - Blog
tags:
    - [Blog, Chirpy, Github, Markdown]

toc: true
toc_sticky: true

date: 2023-08-23
last_modified_at: 2023-08-25
---
## 간단한 마크다운 문법 정리

### **1. 블럭 인용**
```
> 인용문을 사용해봤다.   
첫 줄 이후로는 기호를 입력하지 않아도 블럭이 이어진다.
```
> 인용문을 사용해봤다.   
첫 줄 이후로는 기호를 입력하지 않아도 블럭이 이어진다.

블럭에서 빠져나오려면 줄바꿈을 두 번 하면 된다.
<br>

### **2. 목록**
#### **2. 1. 번호**
1. 오름차순으로 번호를 붙일 수 있다.
2. 들여쓰기를 해도 1-1 등의 번호가 붙진 않는다.
스스로 붙여야 한다.

#### **2. 2. 순서 없는 목록**
`*, +, -`를 이용하여 목록 기호를 붙일 수 있다.
* 이런식으로 순서가 없는 목록도 작성할 수 있다.
    * 들여쓰기로 하위 목록을 만들 수도 있다.
        * 목록 기호의 종류는 3가지이다.
<br>

### **3. 코드**

주로 문법강조를 위해 코드블럭코드를 이용할 것이다.
```java
public class HelloApplication {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

### **4. 링크**
```
Link: [Google](https://google.com, "google link")
```
Link: [Google](https://google.com, "google link")   
간단하다.   
일반적인 url이나 이메일은 알아서 링크를 만들어준다.   
예: <https://naver.com>
<br>

### **5. 강조**
세 가지 강조를 활용해 보자   
```
*Italic*   
**Bold**   
~~Cancel line~~
```
*Italic*   
**Bold**   
~~Cancel line~~
<br><br>

이외에도 사진 등 다양한 문법이 있는데 이건 앞으로 사용하면서 방법을 익혀봐야겠다.   
아직은 자유롭게 글을 작성하기 어렵지만 계속 연습하고 익숙해지면 블로그를 깔끔하게 꾸밀 수 있을 것 같다.