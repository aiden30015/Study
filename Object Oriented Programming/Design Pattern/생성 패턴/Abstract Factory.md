## 추상 팩토리

1. 이해

   > 객체 생성을 캡슐화하여 객체 생성 과정을 추상화하는 패턴이다.

   Abstract Factory pattern은 연관성이 있는 객체 그룹이 있을 경우, 이들을 묶어 추상화하고, 구체적인 상황이 주어지면 factory 객체에서 집합으로 묶은 객체 그룹을 구현하는 생성 패턴이다.

   **연관성이 있는 여러 객체를 구체적인 class에 의존하지 않고 interface를 통해 만들 수 있게 하기 위함**이다. 이를 통해, 클라이언트 코드는 특정 객체를 사용할 때 factory class만을 참조하여 특정 객체에 대한 구현부를 감추어 역할과 구현을 분리시킬 수 있다.

   덕분에, 객체 생성 과정을 쉽게 변경할 수 있다. 예를 들어, 새로운 제품군을 추가하거나 기존 제품군을 변경해야 하는 경우, 클라이언트 코드를 수정하지 않고도 factory class만을 수정하면 된다. 또한, 객체 생성 과정을 추상화하여 유연성을 높일 수 있다. 다양한 제품군을 지원해야 하는 경우, 각 제품군에 맞는 factory class를 생성하여 사용할 수 있다.

   또한 코드의 재사용성을 높일 수 있으며, 테스트에서의 간편성도 높일 수 있다.

2. 사용

   1. python

      ```python
        class Factory:
            def create(self, name):
                if name == "이주언":
                    return 이주언_object()
                elif name == "권재헌":
                    return 권재헌_object()
                else:
                    return None

        class 이주언_object:
            def speak(self):
                return "나는 주언"

        class 권재헌_object:
            def speak(self):
                return "나는 재헌"

        factory = Factory()

        people = factory.create("이주언")
        print(people.speak())  # 출력: 나는 주언

        people = factory.create("권재헌")
        print(people.speak())  # 출력: 나는 재헌
      ```

   2. java

      ```java
        public interface Factory {
            public Object create(String name);
        }

        public class 이주언_object {
            public String speak() {
                return "나는 주언";
            }
        }

        public class 권재헌_object {
            public String speak() {
                return "나는 재헌";
            }
        }

        public class FactoryImpl implements Factory {
            public Object create(String name) {
                if (name.equals("이주언")) {
                    return new 이주언_object();
                } else if (name.equals("권재헌")) {
                    return new 권재헌_object();
                } else {
                    return null;
                }
            }
        }

        public class Main {
            public static void main(String[] args) {
                Factory factory = new FactoryImpl();

                Object people = factory.create("이주언");
                System.out.println(((이주언_object)people).speak());  // 출력: 나는 주언

                people = factory.create("권재헌");
                System.out.println(((권재헌_object)people).speak());  // 출력: 나는 재헌
            }
        }
      ```

   `Factory` class에서 `create` 메소드를 통해 각각 `이주언_object` 또는 `권재헌_object` class의 instance를 생성하고 반환한다. 클라이언트 코드에서는 `Factory()` class의 `create` method를 통해 각각의 객체를 생성하고 사용할 수 있다.

---
