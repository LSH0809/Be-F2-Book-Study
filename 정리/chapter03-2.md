# Chpater 03  자바와 객체 지향 🚀
___
 
## > 2021.10.19 Chapter 3-2 ##

## 정리 ##

- ### 목표 ###
    1. 상속에 대한 이해
    2. 다형성에 대한 이해
    3. 캡슐화에 대한 이해

---

- ### 상속 : 재사용 + 확장 ###
    - 상속을 말 그대로 '상속하다'라는 개념으로 이해하기 보다는 '재사용과 확장'으로 이해해야 한다.
    - 객체 지향에서의 상속은 상위 클래스의 특성을 하위 클래스에서 상속하고 필요한 특성을 추가, 확장해서 사용할 수 있다는 의미이다.
    - '부모 - 자식 클래스'라는 표현 보다는 '상위 - 하위 클래스' or '슈퍼 - 서브 클래스'로 표현하는 것이 적절하다.
    <br>
    - ![image](https://user-images.githubusercontent.com/73347933/137844988-4f06d1f2-c4c9-4d4b-bc24-89e09a1730cb.png)

    - Inheritance(상속) 이라는 키워드는 존재하지 않는다. 대신, extends(확장)라는 키워드를 우리는 사용한다.

    - ### LSP(리스코프 치환 원칙) ###
        - 이론적 정의 : B가 A의 하위 타입일 경우, 상위 타입인 A 객체는 B 타입으로 치환해도, 작동에 대해 문제가 없어야 한다.
        - 다르게 설명해보면, 리스코프 치환 원칙은 '기존 상위 클래스 타입인 A를 사용하던 프로그램이 하위 타입인 B를 이용하여 작동하여도 문제가 없도록 하기 위해서, 하위 클래스는 상위 클래스의 조건 사항을 따라야 한다는 의미이다.

    - ### 상속의 강력함 ###
         ```java
        public class Ex {
            String myClass;
            Ex(){
                myClass = "Ex";
            }
            
            void print(){
                System.out.println(myClass);
            }
        }

        ```
        ``` java
        public class Ex1 extends Ex{
            Ex1(){
                myClass = "Ex1";
            }
        }

        ```
        ``` java
            public class Ex2 extends Ex{
                Ex2(){
                    myClass = "Ex2";
                }
            }

        ```
        ``` java
            public class ExMain {
                public static void main(String[] args) {
                    Ex ex = new Ex();
                    Ex1 ex1 = new Ex1();
                    Ex2 ex2 = new Ex2();

                    ex.print();
                    ex1.print();
                    ex2.print();
                }
            }

        ```
        - 이처럼, 하위 클래스에서 상위 클래스의 메소드를 다시 작성하지 않아도 된다는 것을 확인할 수 있다.
    - ### is - a 관계 ###
        - 상속 관계를 표현하는 더 명확한 용어는 "is a kind of" 이다.
            - ex) 고래 is a kind of 동물 / 조류 is a kind of 동물
        - 객체 지향의 상속은 ...
            1. 상위 클래스의 특성을 재사용하는 것이다.
            2. 상위 클래스의 특성을 확장하는 것이다.
            3. is a kind of 관계를 만족해야 한다.
    - ### 다중 상속과 자바 ###
        - 자바는 인터페이스를 이용해서 다중 상속의 이점만 취했다.
        - 인터페이스를 이용한 상속은 "is a kind of" 보다 "be able to"라는 표현을 쓰는 것이 더 적절하다.(무엇을 할 수 있다.)
            - 인터페이스는 클래스가 "~을 할 수 있다"라는 기능을 구현하도록 강제화한다.
        - 질문)
            1. 상위 클래스는 하위 클래스에게 물려줄 특성이 많을수록 좋을까? 적을수록 좋을까?
                - Ans) 많을수록 좋다. -> LSP(리스코프 치환 원칙)
            2. 인터페이스는 구현을 강제할 메소드가 많을수록 좋을까? 적을수록 좋을까?
                - Ans) 적을수록 좋다. -> ISP(인터페이스 분할 원칙)
                - ISP(인터페이스 분할 원칙)
                    - "클라이언트는 자신이 사용하는 메소드에만 의존해야 한다"를 의미한다. -> 클라이언트로부터 발생하는 다른 클라이언트에게로의 영향을 최소화 할 수 있다.
    - ### 상속과 UML 표기법 ###
        - 상속을 표현하기 위해서는 하위 클래스에서 상위 클래스 쪽으로 화살표를 그린다.
        - 인터페이스를 구현한 경우에는 점선을 이용한다.
        - 인터페이스 구현에 대한 약식 표기로 점선을 이용하기도 한다.
        - ![image](https://user-images.githubusercontent.com/73347933/137852029-29573b5f-dd4c-40ae-a840-aefb96c9e819.png)
    - ### 상속과 T 메모리 ###
        - 상위 클래스 : Animal 필드명 : name 메소드 : showName()
        - 하위 클래스 : Penguin 필드명 : habitat 메소드 : showHabitat()
        ```java
            public class Main01 {

            public static void main(String[] args) {
                Penguin pororo = new Penguin();
                pororo.name="뽀로로";
                pororo.habitat="남극";

                pororo.showName();
                pororo.showHabitat();

                Animal pingu = new Penguin();

                pingu.name="핑구";
                //pingu.habitat="EBS";

                pingu.showName();
                //pingu.showHabitat();

                //Penguin happyfeet = new Animal();
            }
        }
        ```
        
        - ![image](https://user-images.githubusercontent.com/73347933/137853499-04f2411f-7b41-4ffd-a560-151f317e1ce7.png)
---

- ### 다형성 : 사용편의성 ###
    - 오버라이딩 vs 오버로딩
        - 오버라이딩 : 상위클래스가 가지고 있는 메소드를 하위 클래스가 재정의해서 사용

        - 오버로딩 : 동일한 메소드명의 메소드를 여러개 정의하고 매개변수의 유형과 개수를 다르게 정의하는 것
        ``` java
        public class Penguin extends Animal{
            public static String habitat;

            public void showHabitat() {
                System.out.printf("%s는 %s에 살아\n", name, habitat);
            }

            //오버라이딩-재정의: 상위 클래스의 메서드와 같은 메서드 이름, 같은 인자 리스트
            public void showName() {
                System.out.println("어머 내 이름은 알아서 뭐하게요?");
            }

            //오버로딩-중복정의: 같은 메서드 이름, 다른 인자 리스트
            public void showName(String yourName) {
                System.out.printf("%s 안녕, 나는 %s라고 해\n", yourName, name);
            }
        }
        ```
        ``` java
        public class Main {
            public static void main(String[] args) {
                Penguin pororo = new Penguin();

                pororo.name="뽀로로";
                pororo.habitat= "남극";

                pororo.showName();
                pororo.showName("초보람보");
                pororo.showHabitat();

                Animal pingu = new Penguin();

                pingu.name="핑구";
                pingu.showName();
            }
        }
        ```
        - ![image](https://user-images.githubusercontent.com/73347933/137855402-82445670-fa38-4d94-8cba-8792c528da36.png)
        <br>
        - 여기서 주목할 부분은, 핑구의 객체 참조 변수는 Animal 타입이지만, showName() 메소드를 호출하면 오버라이딩된 메소드가 호출된다는 점이다.
        - 즉, 상위 클래스 타입의 객체 참조 변수를 사용하더라도 하위 클래스에서 오버라딩한 메소드가 호출되는 것이다.

---

- ### 캡슐화 : 정보 은닉 ###
   - 접근 제어자
    - ![image](https://user-images.githubusercontent.com/73347933/137857881-74c1af4b-c085-485e-9909-6b8a49529f5b.png)
   - T 메모리
    - ![image](https://user-images.githubusercontent.com/73347933/137857962-6920f6b2-a7ca-4eef-abaf-9ed887d2f815.png)
    - T 메모리에서 보이는 물리적 접근에 따른 이유로 인해 객체참조변수명.정적멤보 보다 클래스명.정적멤버 형식으로 접근해야 한다.
    - ### 참조 변수의 복사 ###
        - Call By Value
            - 값을 복사하는 형식
        - Call By Reference
            - 참조에 의한 호출
        - 하지만, 이는 본질적인 차이가 없다. 
            - 차이는 기본 자료형 변수일 경우 그 값 자체로 해석하는 반면에 객체 참조 변수는 저장하고 있는 값을 주소로 해석한다는 해석의 차이가 있다는 것이다.
            - 아래 ref_a와 ref_b는 다른 변수이지만 같은 객체를 참조하고 있다.
            ```java
                public class Ex {
                    public static void main(String[] args) {
                        Animal ref_a = new Animal();
                        Animal ref_b = ref_a;

                        ref_a.age = 10;
                        ref_b.age = 20;

                        System.out.println(ref_a.age); // 20
                        System.out.println(ref_b.age); // 20

                        System.out.println(ref_a);
                        System.out.println(ref_b);
                    }
                }
                class Animal {
                    public int age;
                }
            ```
            - 따라서, Call by Value와 Call by Reference는 다른 것이라 이해하기보다는 값으로 판단하냐, 주소로 판단하냐로 이해하는 것이 더 쉽고 적절하다.