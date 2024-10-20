## 싱글톤

1. 이해

   > 객체의 instance를 오직 1개만 생성되게 하는 pattern이다.

   Singleton pattern을 따르는 class는 constructor가 여러 번 호출되더라도, 실제로 생성된 객체는 하나이다. 최초 생성 이후에 호출된 constructor는 최초의 constructor가 생성한 객체를 return한다.

2. 사용

   ```python
   class Singleton:
      _instance = None

      @classmethod
      def get_instance(cls):
         if not cls._instance:
               cls._instance = cls()
         return cls._instance

   singleton1 = Singleton.get_instance()
   singleton2 = Singleton.get_instance()

   print(singleton1 is singleton2)  # 출력: True
   ```