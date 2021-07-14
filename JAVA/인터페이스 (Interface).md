

## 인터페이스 (Interface)



### 인터페이스?

* 이중 반복되는 기능들을 쉽게 이용하기 위해 고안됨

* 객체를 어떻게 구성할지 정리한 설계도
* 객체의 교환성(or 다형성)을 높여줌
* 인터페이스 메서드만 알아도 객체 호출 가능
* 객체가 인터페이스를 사용하면, 인터페이스 메서드를 반드시 구현해야 함![img](https://blog.kakaocdn.net/dn/brgAeM/btqN2VpqaBi/kanTFm2nCAyOjYIQL95Bik/img.png)

### 선언

![image-20210714170244073](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210714170244073.png)

```java
interface Alarm {
    public void beep();
    public void playMusic();
}
```

* 구성 멤버 - 상수 필드, 추상 메서드, 디폴트 메서드, 정적 메서드
* 인터페이스의 접근 지정자는 public만 가능
* 객체로 생성할 수 없기에 생성자를 가질 수 없음



### 구현

```java
class SmartPhone implements Alarm {
    public void beep() {
        System.out.println("삐빅");
    }
    public void playMusic() {
        System.out.println("일어나세요");
    }
}
```



## 구성요소

### 상수 필드 (Constant Field)

```java
interface User { //필드타입 상수명 = 값;
    [public static final]
    String FIRST_NAME = "Ryan"; //1
    
    public static final  String FIRST_NAME = "Ryan"; //2 같음
}
```

* 객체 사용 설명서이기에 런타임 시 데이터를 저장할 수 있는 필드 선언 불가이지만 상수 필드는 선언 가능
* 런타임 시 데이터를 바꿀 수 없음
* 상수 선언 시 반드시 초기값을 대입



### 추상 메서드 (Abstract Method)

```java
interface User { //리턴타입 메서드이름(매개변수, ...);
    [public abstract]
    String sendMoney(Money money);
    
    public abstract String sendMoney(Money money);
}
```

* 객체가 가지고 있는 메서드를 설명한 것
* 호출 시 매개값 필요, 리턴 타입이 무엇인지 알려줌



### 디폴트 메서드 (Default Method)

```java
interface User { //리턴타입 메서드이름(매개변수, ...) {...}
    [public] default
    public default void setStatus(Status status) {
        if (status == Status.ACT){
            System.out.println("사용자가 활성화 되었습니다");
            return;
        }
        System.out.println("사용자가 비활성화 되었습니다");
    } 
}
```

* 클래스의 인스턴스 메서드와 동일
* 선언 시 리턴 타입 앞에 default 키워드가 붙음
* Override를 통해 구현 클래스에서 재정의된 인스턴스 메서드로 사용 가능



### 정적 메서드 (Static Method)

```java
interface User { //리턴타입 메서드이름 (매개변수, ...) {...}
    [public] static
    public static void printFirstName() {
        System.out.println("나의 이름은" + firstName + "입니다.");
    }
}
```

* 클래스 정적 메서드와 동일
* 디폴트 메서드와는 달리 객체가 없어도 인터페이스만으로 호출 가능