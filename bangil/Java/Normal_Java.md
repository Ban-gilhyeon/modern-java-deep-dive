
## 2. 객체지향의 특성 

### (1) 캡슐화 
1. 완성도가 있다
   - 기능을 수행하는 단위로써 완전함을 갖는다. 
2. 정보가 은닉되어 있다.
   - 객체의 정보가 밖으로 전달되거나, 밖에서 객체 내의 정보에 접근하지 못하게 한다.  => 객체는 스르로 동작할 수 있는 환경을 갖고 있어야 한다. 외부에 의존하거나, 외부의 침략을 제한하여야 한다.
```java 
class Human{
    //접근지정자로 인한 정보은닉 
    private Heeart heart;
    private Blood blood;
    protected Gene gene;
    
    Blood donation(){
        return this.blood;
    }
}
main{
    Human man = new Human();
Human otherMan = new Human();
 otherMan = man.donation(); // 헌혈을 통한 혈액 기증만 가능 
 otherMan.blood = man.blood; // 임의로 다른 객체에게 줄 수 없음 

}
````
*접근 지정자 : 
- private : 객체 소유.
- protected : 상속된 객체에서도 접근 가능
- (friendly) : 같은 패키지 내에서 접근 가능. (패키지 가시성)
```
com.programmers
com.programmers.girl
com.programmers.girls.Jane
com.programmers.girls.Secret
com.programmers.boy
com.programmers.boy.Tom 
com.programmers.boy.Secret
```
- public : 모두 다 접근 가능 

### (2) 상속
- 상위, 부모 super,`추상`
- 하위, 자식 (this..애매), `구체`

- **오해** : 공통된 기능을 여러 객체에게 전달하고 싶을 때. 
- `원자 > 생물 > 동물 > 포유류 > 사람 > 남자 > 짱구`
### (3) 추상화

- 추상체 : 추상화된 객체 > 부모 클래스로 올라갈 수록
- 구상체 : 구체적인 객체 > 자식 클래스로 내려갈 수록
- 객체간의 관계에서 상위에 있는 것이 항상 하위보다 추상적이어야 한다. 

```java
//의미적 추상체
class Login{
    void login();
}

class KakaoLogin extedns Login{
    void login(){}
}
```

```java
//추상 기능을 가진 객체
interface /*(abstract)*/ lass Login{ //추상 메소드를 하나라도 갖고 있으면 추상 클래스 
    abstract void login();
}

class KakaoLogin extedns /*(implements)*/Login{
   @override void login(){}
} 
 
```

### (4) 다형성 

- 형태(type)가 다양하다. -> 여러가지로 표현할 수 있다
```java
class KakaoLogin implements Login{
    @Override void login(){}
}
//KakoLogin k = new KakoLogin();
Login k = new KakaoLogin();
//필요한 기능만을 제공하기 쉬움 
```

## 3. 객체지향 설계 : 어떻게 하면 객체지향을 잘 할 수 잇는가?
- 객체지향 프로그래밍 : 기능을 객체에게 나눠서 수행시킨다.   
  => 객체를 어떻게 구분했다.  
  => 객체간의 연관 관계가 어떠하다.

- 설명하기 위한 도구 : UML
  - Usecase Diagram
  - Sequence Diagram
  - Package Diagram
  - **Class Diagram**

- Tool : https://draw.io

- 객체지향을 설계하는 5가지 원칙 
- 원칙에 따라서 설계를 하다보니 -> 여러가지 경우에서 공통점을 찾음 -> 디자인 패턴 

[참고 사이트] https://refactoring.guru/ko 

